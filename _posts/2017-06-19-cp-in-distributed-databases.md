---
published: true
title: CP For Distributed Databases
layout: post
date: 2017-06-19 22:46:05
categories: post
tags: cp distributed_systems distributed_databases
comments: true
math: false
---

Some distributed databases are characterized as being [CP](https://en.wikipedia.org/wiki/CAP_theorem). [BigTable](https://static.googleusercontent.com/media/research.google.com/en//archive/bigtable-osdi06.pdf) is an [example](https://www.slideshare.net/GrishaWeintraub/cap-28353551) of this, and it stands in contrast in this respect with [Dynamo](http://cloudgroup.neu.edu.cn/papers/cloud%20data%20storage/dynamo-sosp-2007.pdf) which is AP. If you think about it, however, things are a little bit odd. If you've ever used BigTable or it open-source clone HBase you know that it doesn't stop accepting writes if one node goes down. And at the scale these tools are employed, nodes go down all the time. So is the characterization wrong? Or is there something missing from the description?

In truth, the CAP Theorem is defined in a very precise way. It gives us a whole lot of intuition about the real world, but it does not model it _that_ accurately. It deals with a so-called _read-write register_ - a distributed object which can be _read_ or _written_. This is the entity which can be CP, AP or CA. However, even databases with relatively simple interfaces like the NoSQL key-value stores are much more complicated than a register. For BigTable/HBase a single row (key-value pair) can be assimilated with the register. Indeed, operations on a row happen transactionally, and it is CP in terms of its behaviour.

Physically, the key-space is divided into ranges called tablets. Each tablet it handled by a tablet server, and is replicated three times usually. If a tablet server goes down or if there's a partition, the tablets it handles become unworkable, per the CP behaviour. More precisely, one cannot write successfully, since a write requires all replicas to receive a copy of the data. However, all the other tablets are still OK and the system as as whole is still more-or-less in a functioning state.

What this means in practice is that, for example, a small number of users of the system will see issues, if their data was stored on the failed server. Similarly, not all data in an offline analysis might be available. Which is not the end of the world - as a total shutdown of would imply. And as would happen in a single node database.

A much better article in the same vein is Martin Kleppmann's [Please Stop Calling Databases CP OR AP](https://martin.kleppmann.com/2015/05/11/please-stop-calling-databases-cp-or-ap.html).