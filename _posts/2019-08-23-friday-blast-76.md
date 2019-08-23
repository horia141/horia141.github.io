---
published: true
layout: post
date: '2019-08-23 07:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #76'
---
[Algebraic geometry (2019)](https://johncarlosbaez.wordpress.com/2019/03/15/algebraic-geometry/) - John Carlos Baez is a physics and maths blogger I've been following for some time. Most of the stuff he writes about is way above my pay grade, including algebraic geometry. However this article is about the psychology and sociology of science, and of how to approach difficult subjects, rather than maths per se. And I found it really interesting. And perhaps you will come back to these thoughts when approaching the next _hard_ academic challenge you're facing.

[How to evolve an engineering organisation (2019)](https://lethain.com//how-to-evolve-eng-org/) - some rules for building organisations for companies of different sizes. I've begun reading a big more about management lately. It's a heterogeneous endeavor, but it's nice that some parts of it have more formal aspects.

[Headcount goals, feature factories, and when to hire those mythical 10x people (2019)](https://erikbern.com/2019/02/21/headcount-targets-feature-factories-and-when-to-hire-those-mythical-10x-people.html) - in the same vein of formalising a previously fuzzy domain, we look at hiring and setting the hiring bar in a company, given several constraints - project type, work overhead etc. The result - companies with smaller projects or high work overhead don't need or can't hire _10x_ engineers (excuse the simplification) jives well with reality.

[Graceful shutdown (2019)](http://250bpm.com/blog:146) - I've linked to work on _structured concurrency_ several times in the past. It's one of those things which will be big in 5 years time I think, like async/await is now. In this post the author looks at graceful shutdown of services and how to nicely model this in a structured concurrency framework. What I found interesting was the focus on making the graceful shutdown primitive "composable" - so you can use it alongside other primitives or language constructs.

[Lessons learned scaling PostgreSQL database to 1.2bn records/month (2019)](https://medium.com/@gajus/lessons-learned-scaling-postgresql-database-to-1-2bn-records-month-edc5449b3067) - there's a lot of nice war stories here and a lot of pushing of Postgres. But I feel like the problem could be solved from the root. The author said they wanted a centralised database for _all_ their data, and they wanted to push as much of the processing down to the database. This meant a lot of load on a single DB, a lot of mixed OLTP/OLAP workloads, denormalised views, scripts, ad-hoc message queues, crons etc. Which make sense for smaller DBs, but for huge ones these things break down. They'd have had much better luck going the MySQL/services approach of pushing such logic in separate systems, separate databases etc.
