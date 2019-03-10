---
published: true
layout: post
date: '2019-03-08 07:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #63'
---
[The observability pipeline (2018)](https://bravenewgeek.com/the-observability-pipeline/) - the case for treating metrics/logs/traces data as "another dataset" rather than something different. For example, sending them first to a central collection point (Kafka or equivalent) and then dispersing them to all the "targets" that need them - logging infra, metrics and alerting, even to a data lake so they're available as business metrics. The main idea is to stop `NxM` problems with this data and introduce some decoupling so it's easier to switch infra providers later down the road.

[Extended validation certificates are dead (2018)](https://www.troyhunt.com/extended-validation-certificates-are-dead/) - the message is important - don't waste money on EVs and just use a regular certificate. The rest of this (really long) pieces seems like it's taking the piss on Comodo cybersecurity.

[Whatever happened to the semantic web (2018)](https://www.troyhunt.com/extended-validation-certificates-are-dead/) - remember the "Semantic Web"? It used to be a _thing_. But it never really caught on. What's interesting to me is how the _politics_ of this played out - there were a million standards before there was adoption or even a real killer usecase of the tech.

[TypeScript at Google (2018)](http://neugierig.org/software/blog/2018/09/typescript-at-google.html) - how JavaScript and the whole "frontend thing" evolved at Google vs the rest of the world. An interesting read about the history of this thing and how the author's team is trying to _sync_ Google up with what everyone else uses these days. IMO Google has done this _numerous_ times before it learned the value of open source and building platforms (so before they got serious about cloud). They were doing something way advanced way earlier than anybody else. But they didn't talk about it, or at most released a paper or three. The world picked up on the ideas, and caught up technically, but using their _own stuff_. Examples abound: Hadoop vs MapReduce, HBase/Cassandra vs BigTable etc. And now GCP offers HTable interfaces atop their own infra. Thankfully they're doing good (for them) with Kubernetes and TensorFlow.

[Pixie - a system for recommending 3+ billion items to 200+ million users in real-time (2018)](https://blog.acolyer.org/2018/05/23/pixie-a-system-for-recommending-3-billion-items-to-200-million-users-in-real-time/) - an overview of a Pinterest paper about their recommendation engine. These sorts of things are the backbones of many companies - Netflix, Pinterest, Facebook etc. But they're usually glossed over in ML courses. But they're interesting in their own right and very tricky to get right. So this is an interesting discussion of how the Pinterest teams does it.
