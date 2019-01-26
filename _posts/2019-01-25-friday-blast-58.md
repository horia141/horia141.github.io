---
published: true
layout: post
date: '2019-01-25 07:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #58'
---
[Designations, levels and calibrations (2018)](https://lethain.com//perf-management-system/) - thoughts of Will Larson on the way to structure _career ladders_ as tech companies. This is common stuff for most tech orgs - several ladders, several levels on the ladder and clear guidelines for each level.

[Anatomy of a random number generator (2018)](https://www.masswerk.at/nowgobang/2018/anatomy-of-an-rng) - an analysis of the RNG code of the _first ever_ computer game - Spacewar! from 1959. There's a lot of bang for 10ish lines of code.

[Auto scaling production services on Titus (2018)](https://medium.com/netflix-techblog/auto-scaling-production-services-on-titus-1f3cd49f5cd7) - how folks started using Netflix's Titus for more complicated jobs and how they integrated with AWS to make auto-scaling easy. This is a good lesson to learn - making some thing easy - in this case, running non-critical services in containers - will lead to wide adoption and folks trying to use the service in more and wider ways. So it's good to focus technically on just doing _something_ well and then grow from there.

[A one size fits all database doesn't fit anyone (2018)](https://www.allthingsdistributed.com/2018/06/purpose-built-databases-in-aws.html) - insights from Werner Vogels, Amazon's CTO. Nice overview of the various classes of DB (and what AWS can offer in that space). Also nice how companies like Capital One, Expedia or Zynga built on top of these things some truly monster systems.

[Structured concurrency in high-level languages(2018)](http://250bpm.com/blog:124) - linked with some of the articles on concurrency I wrote about here, this one deals with coroutines and how they behave in higher-level languages - live variables and like program constructs. Also, cancellation pops up as always and _is super important_.
