---
published: true
layout: post
date: '2018-06-15 07:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #42'
---

[Reducing DRAM footprint with NVM at Facebook (2018)](https://blog.acolyer.org/2018/06/06/reducing-dram-footprint-with-nvm-in-facebook/) - Morning Paper's review of a new paper by Facebook on their use of NVM for their MySQL databases. Pretty interesting stuff and a cool production use of non-volatile memory.

[Quantum computing for policymakers and philosopher-novelists (2018)](https://www.scottaaronson.com/blog/?p=3848) - good stuff from Scott Aaronson on what quantum computing will mean for _society_. Many folks focus on cryptography, but machine learning and optimization, and simulation of quantum chemestry are even more important.

[ServiceFabric: a distributed platform for building microservices in the cloud (2018)](https://blog.acolyer.org/2018/06/05/servicefabric-a-distributed-platform-for-building-microservices-in-the-cloud/) - another Morning Paper review, this time of a Microsoft system. It's pretty impressive - sort of Kubernetes on steroids, with a lot of high-availability & routing built in. Still, it's not a PaaS or anything like that, just a service scheduler.

[Full cycle developers at Netflix - operate what you build (2018)](https://medium.com/netflix-techblog/full-cycle-developers-at-netflix-a08c31f83249) - Netflix aims for their developers to be "full cycle" (I imagine this is an extension of __full stack_). This means that they are responsibile for building _and_ running the service. This is pretty common at large Internet companies in fact - Amazon, Google, Facebook etc use it, with SREs doing more infrastructure level work (monitoring a database offered as a service for example). I found the analysis of the pros and cons of this approach interesting as well. Some folks really want to do a certain type of thing, and are going to be frustrated by the full cycle expectation. Though, truth be told, that always comes in the folks who go _deep_. If you're building compilers at one of these companies, yeah, you're probably going to be annoyed by an expectation of monitoring a service. But, most probably, you won't be in that position to boot - you're building compilers. Other folks do like to see the _whole sausage being made_ (myself included).

[The economics of writing a technical book (2018)](https://medium.com/@rothgar/the-economics-of-writing-a-technical-book-689d0c12fe39) - a really insightful look at what it takes to write a book and what a _typical successful outcome_ is. We're not talking about massive successes everyone knows about - TAOCP or the like. Just a regular book about current tech, relatively short and with a moderate shelf-life. And it's not that great. The time committment is huge (year's worth of side-work), but the payoff is kind of meh. Still, it's probably a huge ego boost to write a book.
