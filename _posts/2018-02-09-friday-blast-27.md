---
published: true
layout: post
date: '2018-02-09 06:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #27'
---

[Ten years in, nobody has come up with a use for blockchain (2017)](https://hackernoon.com/ten-years-in-nobody-has-come-up-with-a-use-case-for-blockchain-ee98c180100) - I've been following the blockchain/crypto thing from afar, so I don't have enough context to judge the article. It seems to have a point though, especially when saying that many of the folks who've built one system or another on top of a blockchain, didn't bother to study what they were replacing in detail. And, more importantly, whether the things they'd be giving up had any merit - which, in many cases they did (rewards programs, the ability to dispute charges etc).

[We already know blockchain's killer apps (2017)](https://hackernoon.com/we-already-know-blockchains-killer-apps-f2d443eba35) - a much more bullish overview. Turns out there are killer apps, but of a much smaller scope - digital gold, international payments and "tokenization". Read as a conterpoint to the first link.

[The mess we're in (2014) #talk](https://www.youtube.com/watch?v=lKXe3HUG2l4) - a "seminal" talk by Erlang creator Joe Armstrong. A sober look at all the things we're up against when programming computers - from enormous program state spaces to machine unreliability and failures.

[When "Worst" is best (in distributed systems) (2015) #talk](https://www.youtube.com/watch?v=ZGIAypUUwoQ) - there are certain cases when building a system to handle the worst case actually makes it better for the average case. This isn't mostly the case - building something to scale to 7B people means that the average case of $few people is going to be vastly expensive to handle. But, for example, building something to withstand component failures might make the regular case of no failures even better. For example, by revisiting assumptions about synchronization and coordination and dropping them.

[Developing transactional microservices using aggregates, event sourcing and CQRS (part 1) (2016)](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-1-richardson) and [(part2)](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson?utm_source=infoqEmail&utm_medium=SpecialNL_EditorialContent&utm_campaign=02092017_SpecialNL&forceSponsorshipId=1343) - starting of with a disclaimer: this only applies to _big_ systems. There's a bunch of advantages to a microservices approach to the architecture of a large system. However, one thing which is lost is the ability to do complex transactions - those encompassing entities from multiple domains (user and order and product for example).This article explains how you can get a lot of that back by carefully structuring the application, dealing with DDD's aggregates, employing an event based approach to data modeling (Event Sourcing) and finally separating querying the data from writing it (CQRS). It's a lot of work, but the architecture ends up being cleaner than whatever one would come up ad-hoc at that scale. Of course, one gets eventual consistency in the end, but it's a lot easier to manage it.
