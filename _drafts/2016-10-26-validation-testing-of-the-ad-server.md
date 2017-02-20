---
published: false
---
This article is a little bit of PR for a library I've just released.

I work on the ads team on Stack Overflow. Ironically, we don't have that much to do with the "traditional" banner-style ads on the page. Rather, we take care of the job recommendations which appear on question pages, the front page etc. We like to think of ourselves as the ads team, so I'll use ads terminology. Here's an example of our handiwork:

[ pictures of job ads & company page ads ]

While some of the inner workings of Stack Overflow [links] have been documented elsewhere, much hasn't been said about the ads bits. This post will shed a little light _and_ talk about a recent piece of infrastructure we've open-sourced, a small C# library for _validation testing_ [better name].

## The Problem

Testing hasn't been a big thing at SO. For example, in the ads team we use it quite surgically - we have integration tests which tell us if we can actually perform the basic functionality we say we should do. But there isn't any elaborate testing, or lower-level unit testing, except for some very key bits of infrastructure - some custom serialization/deserialization code, some crypto stuff etc. Adding tests at this point would be a monumental effort, involving both writing a lot of tests and refactoring a lot of code. Both not very fun activities post-facto and for a system which already works. We've also not have many of the problems unit-testing would have caught.

However, there's a class of issues which have affected us, and which testing would have been too little to catch. The poster child for this issue is the following behaviour we have: for some of the ads we have, we have three alternative creatives [ show images ]. Based on their performance, we can deem one as the _preferred_ and serve it with preference. Namely, we'll serve it 90% of the time, and serve the other two randomly. This is a relatively straightforward behaviour to specify. However, the code to actually implement it is spread out in our codebase, there's a lot of special business logic to go around - what if we haven't got the data to show a specific variant, what if [ etc ]. So the behaviour itself is quite hard to test in isolation. But what we're really after is the real-life behaviour evident when we actually serve tends of thousands of impressions for that ad across a day. This is a hard thing to test, but, more precisely, the test behaviour is not what we're after.

This is also something which traditional monitoring is not well suited for. It requires deep insights into our system and a lot of data munging, cleaning and aggregation to get at the insight: the ads which should behave in a certain way are behaving in that way.

There's a bunch of behaviours like this for the ads system. From ad serving to making sure that two services which should have their data in sync actually do so, to just making sure that all the complex business rules encoded in the application are actually reflected in the data.

After a week or so of trying to synchronize the data in our jobs system with the data in our ads system, and finding a myriad issues [1] [integrate this anecdote], I decided to try to build a system which would alert us when something like this happened. From there it expanded into a system for checking all the behaviours of the system, known as ad server validation.

It runs once day, as a scheduled task [Providence?] and looks at the previous day's traffic as well as the totality of the entities in our database.

I managed to extract the runner bits into a small library, useful in other projects. The rest of this post will describe the library, and how to use it.

## Validation

Validation is a library which provides some tools for checking that your complex application is doing the things it's supposed to do. It's a lot like testing, but whereas testing is anticipative, this is post-fact. However, many of the patterns are similar with testing libraries. Where in a testing library like NUnit we have test fixtures and tests, in V we have validation fixtures and validators. V even uses the NUnit fluent constraint bits to assert things about facts. Where things differ is that whereas in NUnit one checks that a function called with some parmeters returns some values, in V, we check that some piece of data in our "model" has some expected value. The model can be anything: entities and tables in an SQL database, entries in a logging system, data in an NoSQL database, values in Redis, files in HDFs etc. as well as anything you can derive from them. Furthermore, if you assert that something is true about the system, and it's true for all the time we're checking it, could you say it's true or false even if the code might be wrong?

As an example, suppose we have a simple bookshop management system. We have books and authors as our entities. We also have a log of which books are sold, and the details of the sale. We're also using microservices, and an books service takes care of the management of books and authors etc, while an orders service takes care of recording sales and doing the coreography of shipping. Not really relevant, just to say that the orders are physically separate from the books, so things such as foreign keys etc. won't be available.

[ schemas ]

There are several things which we'd like to know about our system:

- We have at least one book in our system.
- Books have titles written in "This Format". Operators can enter the title in any form, but we should format this to this format.
- Books should have at least an author.
- Books with three or more authors have the "collective_work" bit set.
- Orders must refer to a book which exists, and with it's properties. Assuming that the book is "static" - has a given price forever etc.

Some of the tests can and should be enforced in the code, and tested via unittests etc. But, as in our SO case, sometimes the code becomes quite convoluted and the simple logic is hidden. So we'd like to just assert a general property about the system.

[ some notes : one writes code that is testable, one should have data that is validationable ]

---
[1] My favorite was a case where we had a parent entity in the jobs system with several child entities which needed to be mirroed on the ads system. Every entity was properly mirrored, but the parent-child relationship was not in several cases. Neither should have been mutable. But they were.