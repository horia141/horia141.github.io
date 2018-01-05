---
published: true
layout: post
date: '2018-01-05 20:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #22'
---

Back from holidays with a shorter set of links. Still, there's some pretty interesting stuff.

[Geospatial indexing: the 10 million QPS Redis powering Lyft (2017) #video](https://www.youtube.com/watch?v=cSFWlF96Sds) - a look at the tools and approaches Lyft uses in order to scale Redis to over 15 million QPS across their whole system. The growth was such that the title of the talk fell behind the actual numbers. It's an interesting approach of high-level algorithm design (S2 based geohashing, complex business rules around position updates and reads) and basic infrastructure tailored to Lyft's specific issues (proxies with consistent hashing, service discovery, health checks).

[Reasoning about performance in the context of search (2017) #video](https://www.youtube.com/watch?v=80LKF2qph6I) - again a deep dive into the design of search (or at least some aspects of it) at Bing. The usage of Bloom filters is quite interesting, as opposed to the usual inverted index / post lists. I'd say the best thing to get out of this talk is the way the author goes about estimating performance for several cases, and how even from high level numbers (I want to serve 10M documents) one gets to pretty low-level details (that means I'll do 5 memory accesses on average). The kind of stuff which should be considered when designing anything performance sensitive. And also the kind of stuff which frequently pops up in system design interviews.

[Why your encrypted database is not secure (2017)](https://blog.acolyer.org/2017/06/16/why-your-encrypted-database-is-not-secure/) - turns out databases leak a lot of information in various memory and disk caches, access logs etc, which can be used by local attackers to beat the data encryption in so called _encrypted databases_. This even occurs in the form of _snapshot attacks_, which are attacks where one can see just one query. Another thing to add to your "securing data at rest is a hard problem" box.

[Service ownership checklist (2017)](http://codecapsule.com/2017/11/12/service-ownership-checklist/) - a an example of a service ownership checklist - all the bases you need to cover when you're running a service for other teams / external user. Spans subjects from project management to security, logging, capacity planning etc. The list is kind of daunting, but then again, it's applicable to more mature organizations, which can take the time to properly do these things.

[The art of promise-based architectures (2015)](http://blog.rangle.io/the-art-of-promise-based-architecture/) - in JavaScript land there is (or was) a big transition from callbacks to promises and later to `async/await` on top of those promises. This is an article from the start of that transition highlighting the benefits and how to think in the new world.


