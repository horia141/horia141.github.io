---
published: true
layout: post
date: '2017-09-29 2:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #11'
---

This is the 11th installment of the Friday Blast series. More data science and career advice this time.

[Should robots pay taxes (2017)?](https://hackernoon.com/should-robots-pay-tax-a2578bdf9f38) - the answer to question in titles is usually "no", but this time it seems to be "yes". We all know the [robot apocalypse](https://en.wikipedia.org/wiki/AI_takeover) is coming. The realistic way it'll happen is the swift replacement of human labor, both knowledge work and manual work, with that of robots. We've of course seen this before with the industrial revolution and all that followed, and we managed to get by. It's less clear that this is going to be the case this time without big changes in how we as a whole operate. The article talks to a certain extent about various solutions, and to a larger extent about a "robot tax". This would basically be a tax on the owners of capital - corporations more or less - for the non-humnan workers they have. It's very low on a totem pole which includes things like universal income, but it seems better than Luddite answers of not dabbling in AI and letting things just be.

[Three paths in the tech industry: founder, executive, employee (2017)](https://blog.ycombinator.com/three-paths-in-the-tech-industry-founder-executive-or-employee/) - this comes from the Y Combinator blog so you know it's good stuff. The article goes into details about the pros and cons of each approach to building a career in tech, as well as specifying a handy set of strategies to actually getting there. There's a certain focus on working in big tech companies or succesfull startups of the Sillicon Valley kind, but I would not say it is overpowering. I really liked the realistic approach to this. It's not focused on tech chops or visionary ideas. But rather on more mundane stuff like the ability to communicate, build teams and consensus and play the required political games. The last paragraph is quite sobering. It's going to take roughly 10 years to get _good_ at any of the paths, so you can't afford to dilly-dally.

[An intuitive guide to linear algebra (2013)](https://betterexplained.com/articles/linear-algebra-guide/) - part of a series on [BetterExplained](https://betterexplained.com/) about mathematics, this piece deals with some aspects of linear algebra. It's pretty well done and most anybody will get something from it, but it's also quite short. There's a lot more intuition to build in linear algebra.

[Three best practices for building successful data pipelines (2015)](https://www.oreilly.com/ideas/three-best-practices-for-building-successful-data-pipelines) - gaining and using the insights from data is becoming more and more crucial to many businesses large and small. In order to do this reliably one has to treat the problem as an engineering one, besides a statistics one. This means that the _data pipeline_ - that system which turns the raw data like visit logs and purchase records into insights like user recommendations and analytics - needs to be carefully crafted. The three properties the authors recommend is that it be reproducible, consistent and productionizable. The first means that is all the tools and assumptions should be stored safely in source control and reused in a controlled manner for each run. This ensures that two runs on the same input produce the same output. The second means that there should be a way of keeping inputs in a "pristine" state which isn't modified past the initial generation. This ensures that you actually have something to run the reproducible programs a second time on. The third means that good software engineering practices are followed - common code is split into libraries, there's a proper runtime definition with explicit dependencies etc, metrics are collected, alerting is in place etc.

[Using logs to build a data infrastructure (2016)](https://www.confluent.io/blog/using-logs-to-build-a-solid-data-infrastructure-or-why-dual-writes-are-a-bad-idea/) - the idea of logs - append only structures for recording events - crops up in a lot of different places. The article goes into details about organizing your whole system's architecture around logs. Every event generated would go to a log. After which, various systems, such as databases, caches, search indexes etc. would read the logs, preferably in near-realtime and update their state. Such architectures are attractive because it places the log at the center of integration and the log is very simple and high-performance. We'd be turning $$O(N^2)$$ to $$O(N)$$ integrations. It's not all perfect though. Issues of transactions and of breaking the favourite `read_request -> write_to_db -> respond_with_new_data_from_db` / read-your-writes consistency crop up.

[Making the case for building scalable stateful services in the modern era (2015)](http://highscalability.com/blog/2015/10/12/making-the-case-for-building-scalable-stateful-services-in-t.html) - here's an interesting idea. The common mantra when building internet applications is to put anything that smells of application logic into a stateless service layer which sits between clients (which are also stateless) and various storage systems. The latter _are_ not stateless, beacause something has to hold the state. But they're generally off-the-shelf components like databases and caches which are tuned to the specific problem. This is sound advice for most cases and it _does_ make building applications a whole lot easier. But it has performance drawbacks. And sometimes you can't afford those. And this article describes how certain systems are _helped_ by going stateful. However, this isn't your grandpa's _statefulness_. There's a lot borrowed from database research. Gossip protocols, consistent hashing, cluster membership etc. all make their appeareance. All the more reasons to study these things - at some point you might be called to implement a subset of them for a service layer. This seems much like state in a programming language context. Most of the time it's easier and less bug-prone to think about transformations of immutable data structures. But you have to do state _at some point_ and usually because of a performance constraint.