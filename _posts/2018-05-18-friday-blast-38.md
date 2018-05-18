---
published: true
layout: post
date: '2018-05-18 07:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #38'
---

Another batch of random links.

[Event sourcing with Kafka (2018)](https://dzone.com/articles/event-sourcing-with-kafka) - continuing the Event Sourcing discussion from last week, here's a quick sketch of how to do it with Kafka and Kafka streams. It's for larger scale projects to be sure, but an interesting approach.

[Building a text editor for a digital first newsroom (2018)](https://open.nytimes.com/building-a-text-editor-for-a-digital-first-newsroom-f1cb8367fc21) - a hit from some time ago, this one describes the rebuilding of the New York Times' custom built CMS editor. What's interesting is the _scale_ at which the NYT operates - multiple teams spread across the globe, loads of writers, a _lot_ of customization and a very complicated setup overall. A barebones WordPress this ain't.

[PostgreSQL's fsync() surprise (2018)](https://lwn.net/Articles/752063/) - yet another issue with `fsync` - this time caused by OSes. In certain situations, if there's an error writing pages to disk, the error gets lost and Postgres doesn't know about it. Scary stuff. And ties into the previous discussion that sometimes having a distributed database helps you avoid problems like this. You _know_ a replica of yours managed it store something, but apparently you can't extend the same trust to the disk.

[You don't need a CS degree to be a successful engineer, but it helps (2018)](https://www.getdrip.com/broadcasts/166594061/c3628fcd3c81a04dce8cf) - a collection of the author's past experience where some extra CS knowledge would have helped understanding or solving a problem. There's a bunch of them, but I think we all have some stories like that. The bottom line is that the _knowledge_ earned during a CS degree usually has a high shelf-life and you should somehow learn it if you did not take the traditional route. Now, whether the 3-4-5 years it takes to do the degree and the whole experience are worth it, is another question ...

[Myths programmers believe about CPU caches (2018)](https://software.rajivprab.com/2018/04/29/myths-programmers-believe-about-cpu-caches/) - a bunch of good stuff here. Especially nice debunking the "We need synchronization / memory barriers because different caches might have different data". At least on x86s that's not the case - caches are always consistent. Not so registers though.

[Continuous integration and feature branching (2018)](http://www.davefarley.net/?p=247) - a case against using feature branches (or more precisely, long lived feature branches) when doing continuous deployment or integration. The main argument is that you're not really "integrating" anything if you're storing 2-5-8 versions of the system at the same time and for weeks or months at a time. You should be continuously updating master/trunk and always having a system which works - whether by feature flags or just not calling the new code etc.
