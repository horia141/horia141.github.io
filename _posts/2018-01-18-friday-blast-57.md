---
published: true
layout: post
date: '2019-01-18 07:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #57'
---
[A short guide to hard problems (2018)](https://www.quantamagazine.org/a-short-guide-to-hard-problems-20180716/) - most folks are familiar with the P and NP _complexity classes_, at least via the `P vs NP` problem at the core of computer science. Here a bunch of extra complexity classes are covered - BPP, BQP, PH, PSPACE and EXPTIME as well as the relationships between them. Sometimes they're clear cut, other times we have strong reasons to believe a they're the same, and yet other times the field is open.

[Introduction to model trees from scratch (2018)](https://towardsdatascience.com/introduction-to-model-trees-6e396259379a) - one of the cooler aspects of computer science inspired ML models (decision trees and neural networks[1]) is that they're oftentimes "composable". Here the space partitioning approach used in decision trees is combined with linear regressions at the leaves, to produce a more powerful model than the "classic" constant model one.

[AWS, MongoDB, and the economic realities of open source (2019)](https://stratechery.com/2019/aws-mongodb-and-the-economic-realities-of-open-source/) - as usual, a good piece from Stratechery on the business side of tech. This time with a focus on open source. It's been a _thing_ for the last 2-3 years that tech companies in the open source infrastructure space were in for a tough time because cloud providers were offering their systems in a more convenient and cheap way. Docker, ElasticSearch, Redis, MongoDB, Hadoop and their backing companies were prime examples. This article focuses on MongoDB and Mongo Inc. But it's telling. Companies in this space need to move up the value chain if they're going to succeed. I plan on writing my own bit on this shortly.

[A primer on database replication (2017)](https://www.brianstorti.com/replication/) - the various approaches to data replication in the database context. It's nice that it looks at both SQL and NoSQL solutions and how each tackled the problem.

[Billions of messages a day - Yelp's real-time data pipeline (2016)](https://engineeringblog.yelp.com/2016/07/billions-of-messages-a-day-yelps-real-time-data-pipeline.html) - a description of the impressive architecture Yelp has deployed to organize it's systems. A Kafka based central data repository is not that _future-tech-y_, and I've posted about such an approach several times here. But the central schema store with built-in tracking of streams, documentation and integration with code is pretty sweet.

---
[1] As opposed to statistics inspired ones - GLMs, SVMs etc.
