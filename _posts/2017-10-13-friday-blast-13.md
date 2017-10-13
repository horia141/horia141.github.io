---
published: true
layout: post
date: '2017-10-13 10:30'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #13'
---

This is the 13th Friday Blast post. Coincidentally[1] today is also Friday the 13th. 

[Fature Toggles (2016)](https://martinfowler.com/articles/feature-toggles.html) - feature toggles is a set of patterns which allows not-yet-ready code to exist in an application, without having any effect. This article describes in a wealth of details usecases, types of toggles, infrastructure support etc. for them.

[How to safely store a password (2010)](https://getpocket.com/redirect?url=https%3A%2F%2Fcodahale.com%2Fhow-to-safely-store-a-password%2F&formCheck=c6f4865ffdcf1e165221e221555f47b3) - use a _password hash_, like `bcrypt`, `scrypt` etc. There's more to it than that, as previous links in this series have highlighted, but a quick reminder is always welcome I think.

[The binary search of distributed programming (2015)](http://antirez.com/news/102) - is generating a strictly increasing sequence of integers/IDs. Which turns out to be pretty hard, in general. Which tells you a lot about distributed systems - something achievable with a single counter and possibly some locks on a single machine becomes very hard in a distributed setting. The author is also the author of Redis, so he know a thing or three. But the algorithm proposed seems to be broken or at least provide some bad guarantees. In any case, a good read about designing these things and what can go wrong.

[Take it to the limit: considerations for building reliable systems (2016)](http://bravenewgeek.com/take-it-to-the-limit-considerations-for-building-reliable-systems/) - mainly advice on building distributed systems. This time, having to do with "limits" and enforcing them. Basically, wherever and whenever there's some quantity in the system which might grow unbounded, you should have hard limits on it. Request sizes, queue depths, items to process, child entities for a parent entity, response sizes etc. should all be limited somehow. This protects against malicious agents trying to DoS the system, but also against your own agents doing the same.

[A five muntes guide to better typography (2017)](http://pierrickcalvez.com/journal/a-five-minutes-guide-to-better-typography) - a piece about graphic and typographic design.

[Difference between a clustered index see and non-clustered index seek (2016)](https://dba.stackexchange.com/questions/137724/difference-between-clustered-index-seek-and-non-clustered-index-seek/137731) - a StackOverflow question. There seems to be this misconception that non-clustered indices are slower than clustered ones, since one has to do a seek/scan, then another seek for the data itself. But depending on how large the data is and how compact the non-clustered index manages to be, this might not be the case. Since the first seek/scan might occur completely in memory, or at least touch less pages than the clustered one. Ditto, for counting queries, a non-clustered index might be much faster.

[The map of mathematics #video (2017)](https://www.youtube.com/watch?v=OmJ-4B-mS-Y), [The map of computer science #video (2017)](https://www.youtube.com/watch?v=SzJ46YA_RaA), [The map of physics #video (2017)](https://www.youtube.com/watch?v=ZihywtixUYo), [The map of chemestry #video (2017)](https://www.youtube.com/watch?v=P3RXtoYCW4M) - a really wonderful set of videos laying out the "branches" of the mathematics, computer science, physics and chemestry. It's a really big picture view, and as the author himself notes, everything is more or less interconnected within and across fields, but it's still nice to see all of the pieces of knowledge which are somehow distinct enough to be called something. The animation is really great as well.

---
[1] Or not :o
