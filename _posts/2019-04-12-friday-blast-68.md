---
published: true
layout: post
date: '2019-04-12 07:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #68'
---
[Why we build CockroachDB on top of RocksDB (2019)](https://www.cockroachlabs.com/blog/cockroachdb-on-rocksd/) - an insightful post from the CockroachDB team about how they use [RocksDB](https://rocksdb.org/) as the storage layer for single nodes. RocksDB is a embedded KV-store in the vein of LevelDB, Sqlite etc. which uses [LSM](https://en.wikipedia.org/wiki/Log-structured_merge-tree) storage. For me it's also interesting how this separation seems to be more-and-more common. Use a well known storage layer, and build only the value-added thing on top of it. Especially since said storage layer would deal with platform idiosyncrasies like `fsync` bugs etc. MySQL and even Postgres have been used this way, but they're obviously more heavyweight.

[Exploring distributed systems theory: availability and consistency (2019)](https://hackernoon.com/exploring-distributed-system-theory-availability-and-consistency-e8c59e0875cd) - a nice read overall for linking the abstract (and fuzzy) nature of the CAP theorem with the real systems you'll see. The best part was the discussion of a "CP" system like etcd/ZooKeeper and how trading off Availability just means not being able to have "perfect" availability - responding to _every_ query with some sort of success data. But not going into "stupid"" availability - like not responding to _any_ query. Systems like that usually are deployed in groups of `3` or `5`. And when a partition occurs, they're designed to choose consistency. So the nodes outside the quorum won't be able to handle writes - hence they won't be _available_. But the system as a whole is still in a _decent_ functioning state of _reduced_ availability.

[The end of the beginning #youtube (2018)](https://www.youtube.com/watch?time_continue=7&v=RF5VIwDYIJk) - a presentation by Benedict Evans from Andreessen Horowitz on the "future" of _tech startups_ (as they know them at least). The main idea is that while IT has managed to affect a great deal of fields - with the biggest winners being in ecommerce and advertising - we haven't even scratched the surface of what could be done. The hard part only comes from here in fact, but there's the potential of affecting the whole global economy, from agriculture to logistics and medicine.

[Kubernetes in 5 mins #youtube (2017)](https://www.youtube.com/watch?v=PH-2FfFD2PU) - what it says on the box. A short guide for what is useful about K8s.
