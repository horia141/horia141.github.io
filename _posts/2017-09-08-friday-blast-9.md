---
published: true
layout: post
date: '2017-09-08 10:32'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #9'
---

The 9th installment of the Friday Blast series. A slight focus on physics for this week.

[What is a field really? (2011)](https://physics.stackexchange.com/questions/13157/what-is-a-field-really) - a [Physics StackExchange](https://physics.stackexchange.com/) question. My physics education leaves much to be desired. And I've always been confused by the concept of _field_. Turns out it's quite simple - it is just a way of describing some physical phenomenon which occurs over every point in space and varies with time. So basically a function $$F(x,y,z,t)$$ which can be scalar, vectorial, tensorial etc. The examples with temperature and wind from the second answer are especially instructive, since they're easier to relate to than electromagnetic fields.

[Intro to SDR and RF signal analysis (2017)](https://www.elttam.com.au/blog/intro-sdr-and-rf-analysis/) - this article prompted me to explore the previous question about fields actually. The most interesting parts the reverse-engineering of various wireless devices' communication with GNU radio tools.

[The fundamental limits of knowledge (2015)](https://medium.com/starts-with-a-bang/throwback-thursday-the-fundamental-limits-of-knowledge-200b10b86c8) - the discussion here was way over my head. I had expected it to be about things that can be proved or not, or things like that. But it turns out that there's a bunch of stuff about the Big Bang and the very earliest moments of our Universe, which we can't ever know, because that information was permanently lost. Interesting stuff.

[The microservices cargo cult (2015)](https://www.stavros.io/posts/microservices-cargo-cult/) - when microservices became a thing 2 or 3 years ago, everybody and their grandmother seemed to be caught in the hype. Things have calmed down a bit in the meantime[1]. This article was written during the height of the hype period and reminded people that there's some pretty hefty operational costs to running a microservices system and people shouldn't employ this architecture lightly. Things have improved a little bit, in the sense that there are a bunch of mature monitoring, logging etc. providers right now which can ease building such systems from the get-go rather than when you reach _operational maturity_. But still, sage advice.

[Lessons learned writing highly available code (2015)](https://medium.com/imgur-engineering/lessons-learned-writing-highly-available-code-7eaf3d7aae00) - we've had these sorts of tips here on Friday Blast before, but they're always welcome. In short: have timeouts for RPCs, have exponential backoffs for retries, have multiple levels of health checks and watchdogs and generally _limit_ everything that can come from a _user_ (data requests, open connections, timeouts etc). Perhaps the _sagest_ advice is to use battle tested tools rather than the _new hotness_. 

[Using atomic transactions to power an idempotent API (2017)](https://brandur.org/http-transactions) - an example of building a small user database for a webapp and ensuring emails are unique via transactions alone. It's a nice example of the benefits of using the _SERIALIZABLE_ isolation level of a database. Unfortunately not many people are aware of isolation levels and the ability to tune-them by transaction. A small nitpick - they're using _isolation_ rather than _atomicity_ from ACID here. Isolation ensures that transactions execute without stepping on each other's toes - as if each was executing alone on the DB. Atomicity just ensures that the transaction either succeeds fully or fails fully, but doesn't leave the DB in an inconsistent state. There's also a nice discussion about getting events data out of the DB to other systems via a periodic task rather than a perilous double write.

[The unreasonable effectiveness of Random Forests (2015)](https://medium.com/rants-on-machine-learning/the-unreasonable-effectiveness-of-random-forests-f33c3ce28883) - there's more to machine learning than Neural Networks. Shocking right? After linear models, a workhorse of the field is tree models and their Random Forest realisation. There isn't anything super technical here, but there's a good overview of their pros and cons. They're not the best choice when you're dealing with _signal_ data, but for other modalities I think they're often overlooked for data hungry and resource intensive neural networks. And that's a shame, because they're quite nice models and they have a good theoretical background.

---
[1] We now have serverless though to take the heat.
