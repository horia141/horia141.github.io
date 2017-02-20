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

It runs once day, as a scheduled task [Providence?] and looks at the previous day's traffic as well as 

---
[1] My favorite was a case where we had a parent entity in the jobs system with several child entities which needed to be mirroed on the ads system. Every entity was properly mirrored, but the parent-child relationship was not in several cases. Neither should have been mutable. But they were.