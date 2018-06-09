---
published: true
layout: post
date: '2018-06-08 07:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #41'
---

[Probit regression (2018)](https://www.johndcook.com/blog/2018/05/05/probit-regression/) - this is an alternative to the more famous [logistic regressions](https://en.wikipedia.org/wiki/Logistic_regression). They're both generalized linear models, and the difference lies with the _link function_. For the first it is the so-called _probit_ function, while for the latter the _logistic_ one. The probit function is the inverse of the standard normal distribution's CDF. It looks very much like the well known logistic link-function / neural activation function, and in practice the two method are basically the same. But sometimes it's easier to analyze with one than with another.

[Introduction to decision tree learning (2018)](https://heartbeat.fritz.ai/introduction-to-decision-tree-learning-cd604f85e236) - covers what the models looks like as well as a sketch of a learning algorithm (ID3 in this case).

[Oracle plans to dump risky Java serialization (2018)](https://www.infoworld.com/article/3275924/java/oracle-plans-to-dump-risky-java-serialization.html) - I've heard a lot of good stuff from Java world lately and it seems the language is moving faster than ever. Dropping serialization is a _big_ move, and it'd be interesting to see it play out. If I hadn't moved to other pastures in the meantime.

[The headers we don't want (2018)](https://www.fastly.com/blog/headers-we-dont-want) - an analysis done by Fastly on the common headers they encounter. Turns out there's a lot of popular but otherwise useless ones. The author selects vanity, deprecated standards, debug and plain old misused headers for special attention. There's an example of VCL - Fastly's small language for request transformations. Whic his pretty neat.

[Malloc never fails (2012)](https://scvalex.net/posts/6/) - yes it does, but in Linux you'll be killed by the kernel before you get a chance to react. So it still doesn't make sense to try to treat this particular failure case in most situations. What is interesting is that even if it succeeds you're not guaranteed the memory - just when you start using it. So you can allocate a bunch more than you could actually use - and will only crash when you _do use_ it.
