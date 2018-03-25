---
published: true
layout: post
date: '2018-03-23 13:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #33'
---

[Measuring transactional integrity in AirBnB's distributed payments ecosystem (2018)](https://medium.com/airbnb-engineering/measuring-transactional-integrity-in-airbnbs-distributed-payment-ecosystem-a670d6926d22) - AirBnB has a whooping number of payments integrations of all sorts - APIs, redirect flows and good ol' FTP uploads. Even in the simplest cases this is a system which takes a while to achieve consistency and some notion of "data integrity". So the payments team have setup a number of extra monitoring systems to look at issues and produce metrics of the "health of payments subsystem". I've been thinking of issues related to this a lot in the past year. In many systems, it's not enough to have a strong type system and a battery of tests in order to be certain of a system's correctness. You need to actively look at the system's state and find the issues. This might mean checking that invariants which are hard to express in code or business rules which aren't concisely expressed in code are maintained.

[The problem with Webpack and why it is (kind of) our fault (2018)](https://medium.com/@allanbaptista/the-problem-with-webpack-8a025268a761) - Webpack is a great tool. The author makes the point - and I agree with it - that it _changes_ too much. And the change is in a very haphazard way - there's many breaking changes and many changes of course. It's my view that the tool started out very flexible, in a way similar to Gulp/Grunt and friends, but then, as common patterns emerged for using it, as well as the ecosystem evolving as a whole, things became codified as standard behaviour rather than being provided by a plugin. It's tough to follow with changes from major versions. Hopefully things will calm down and folks will cut the tool some slack.

---

The following is a series of 5 articles on the design process involved in building a distributed log a la Kafka.

[Storage mechanics (2017)](https://bravenewgeek.com/building-a-distributed-log-from-scratch-part-1-storage-mechanics/) - covers the problem and design space for it as well as lays out how a _node_ in the distributed log would work. One question I had was about ensuring writes are durable via `fsync` or similar mechanisms. I just though it was an omission, but part 2 clarifies it.

[Data replication (2017)](https://bravenewgeek.com/building-a-distributed-log-from-scratch-part-2-data-replication/) - deals with replicating the data from that single node to multiple ones. Mostly for redundancy. The `fsync` issue is _solved_ in a nice way. Durability is ensured via replicating to different machines rather than ensuring the write is durable to disk. This is both _safer_, _faster_ and actually works. Disks are notorious for the shenanigans they do to get performance, and many times they sacrifice correctness - even after an `fsync` you aren't 100% the data is saved. Other than some discussion on quorum vs master+all-replicas is done and a presentation of what Kafka (ad-hoc consensus) vs NATS (Raft) do.

[Scaling message delivery (2018)](https://bravenewgeek.com/building-a-distributed-log-from-scratch-part-3-scaling-message-delivery/) - this one talks about how to spread data on multiple machines via sharding (as opposed to the replication of part 2). There's some coverage of pull vs push methods and consumer scalability.

[Trade-offs and lessons learned (2018)](https://bravenewgeek.com/building-a-distributed-log-from-scratch-part-4-trade-offs-and-lessons-learned/) - basically what they'd have done different in NATS had they had the benefit of hindsight.

[Sketching a new system (2018)](https://bravenewgeek.com/building-a-distributed-log-from-scratch-part-5-sketching-a-new-system/) - how the author would go about building a new system based on NATS, but taking to heart design cues from Kafka anad NATS streaming.
