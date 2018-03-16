---
published: true
layout: post
date: '2018-03-16 13:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #32'
---

[Microservice fallacies (2016)](https://www.infoq.com/news/2016/10/microservices-please-dont?utm_source=infoqEmail&utm_medium=SpecialNL_EditorialContent&utm_campaign=02092017_SpecialNL&forceSponsorshipId=1343)- the usual stuff - only get them once you're sure you need them. Which is usually _not_ at the start of a project. There's other ways to get the modularisation benefits.

[A programmer's guide to polynomials and splines (2018)](http://wordsandbuttons.online/programmers_guide_to_polynomials_and_splines.html) - this is mostly about interpolation and figuring out nice polynomials for various interpolation tasks. This sort of material is sometimes lumped in with other regression tasks in a statistics/ML course, so it's interesting to see them from a more "engineering" point of view, without the probability theory.

[Security 101 for SaaS startups (2017)](https://github.com/forter/security-101-for-saas-startups/blob/master/readme.md) - some advice on security for SaaS companies. It's nice that it focuses on company-wide issues such as using 2FA for employee accounts, besides the standard advice on encrypting data and using password hashes etc.

[Smart endpoints, dumb pipes (2017)](https://bravenewgeek.com/smart-endpoints-dumb-pipes/) - another neat article from Tyler Treat. It's about the issues in distributed systems around resiliancy and exactly once delivery. The point hammered is that these things are properties of the application as a whole, rather than a particular infrastructure component. And the point where you want to control this is usually the "endpoints" - that is the services making use of your infrastructure. The counterpoint is that embedding smartness in "middleware" - message queues, distributed databases etc. will lead to (1) bad performance, since the middleware will need to "fat" and handle a lot of the complexity itself. Even when that isn't required. Secondly, it'll give you a false sense of security. Because the properties are application level, you really can't protect at a lower-level - that is, do something like proper deduplication of events without some context from the application of what is a duplicate and what is not. Building distributed systems - still hard.
