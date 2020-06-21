---
published: true
layout: post
date: '2020-06-21 07:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #86'
---
It's been quite some time since one of these. It's more like a monthly blast for a while. I'll try to do better
in the future.

[What does technical excellence look like (2016)](https://www.youtube.com/watch?v=Avs70dZ3Vlk) - Martin Fowler
takes stock of what _technical excellence_ means. To summarise it is short cycle times for building features,
low time to fixes (and the CD these imply), small and autonomous and business driven teams, and teams where
there is a high degree of psychological safety.

[From "Hello World" to VP Eng (2017)](https://blog.devcolor.org/career-journey-part-1-3bdddf1f87a) - the first
part of Nick Caldwell's story, Reddit's VP of engineering.

[Scaling SQLIte to 4M QPS on a single server (EC2 vs Bare Metal) (2018)](https://blog.expensify.com/2018/01/08/scaling-sqlite-to-4m-qps-on-a-single-server/) - in case
you doubted just how powerful modern machines are, and how much of a beast SQLite is. It's of course a somewhat
artificial benchmark, but not completely so. For my [jupiter](https://horia141.com/announcing-jupiter-0.3.0.html
) work I'll soon be transitioning to a SQLite backend for local data storage.

[DDD and hexagonal architecture (2020)](https://vaadin.com/learn/tutorials/ddd/ddd_and_hexagonal) - I've recently
started reading a bit more about software engineering, and software architecture in particular, and domain driven design
(DDD) caught my eye as a powerful way of thinking about architecture. It's kind of hard to grok however at the
implementation level and this article from [Vaadin](vaadin.com) does a very thorough job of this.

[Tactical domain-driven design (2020)](https://vaadin.com/learn/tutorials/ddd/tactical_domain_driven_design) - linked
with the previous article is this one, which goes into the details of the "domain" aspect of DDD (the part which is
usually not tied into any framework or library), and which covered the _tactical_ patterns employed in DDD.
