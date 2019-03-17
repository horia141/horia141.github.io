---
published: true
layout: post
date: '2019-03-15 07:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #64'
---
Made it to $$2^6$$ Friday blasts!

[Lies programmers believe about calendars (2018)](https://boingboing.net/2018/09/27/corner-cases-everywhere.html) - fun little article about the complexities of dates, times and calendars. The topic's been covered here before. This stuff is super complex because people keep changing stuff all the time. Almost anything you could think of has a counter example - even time running "forwards".

[The history of infrastructure at Zendesk - constant tradeoffs (2018)](https://medium.com/zendesk-engineering/the-history-of-infrastructure-at-zendesk-constant-tradeoffs-bdfa916ff4c3) - Zendesk seem to be doing a lot of interesting stuff as a "service at scale". Interesting with their take on AWS and the constraints they had which lead to not using it. Basically they were always a bit bigger that what AWS could offer so it made sense to use something else.

[The design and implementation of modern column-oriented database systems (2018)](https://blog.acolyer.org/2018/09/26/the-design-and-implementation-of-modern-column-oriented-database-systems/) - an overview of a paper I _should_ read at some point. Columnar DBs are the workhorses of analytics workloads. This article covers some design approaches for them. Compression, bitmap indices and even direct operations on compressed columns are some of the key requirements for good/great performance.

[Marmaray: an open source generic data ingestion and dispersal framework and library for Apache Hadoop (2018)](https://eng.uber.com/marmaray-hadoop-ingestion-open-source/) - Uber's "data ingestion" library. Uber's "data system" has been featured on the blog before. It's interesting in itself - Uber is a big tech company, but with a very narrow focus, so these sorts of systems tend to be very specific to them. The main problem is that of controlling how data gets "ingested" and stored. There's multiple producers (Kafka, MySQL tailing, Cassandra etc.) and multiple consumers (S3, HDFS, Cassandra, etc). In order to avoid an `NxM` problem, Marmaray was designed. It's a system atop Spark which controls ingestion (reads) and dispersal (writes). It's also centralised and operated by a single team and offered as a service to other teams.
