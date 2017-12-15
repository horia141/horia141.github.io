---
published: true
layout: post
date: '2017-12-15 08:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #21'
---

[Online migrations at scale (2017)](https://stripe.com/blog/online-migrations) - an article from Stripe engineering about how they performed a large-scale migration of their core data structures without any downtime. Now, not all migrations are this complex, but some are. And in this particular case, in any setup you'd have - large or small - you'd be stuck doing the same dance. I found the use of [Scientist](https://github.com/github/scientist) to be particularly interesting. This is a Ruby library which aids in refactoring data paths - they made sure that all of their new read paths produced the same results as their old read paths, and had extensive error reporting and monitoring around it.

[Why configuration management and provisioning are different (2017)](https://www.thoughtworks.com/insights/blog/why-configuration-management-and-provisioning-are-different) - an article from ThoughtWorks on the differences between the two. Provisioning deals with building the infrastructure for a project: booting machines, setting up networks, roles in IAM etc. So it is a global concern. Configuration management deals with making sure a single machine is configured: setting up the OS, firewall rules, patches etc. So it is a local concern. The author expresses concern over people confusing the two, and using configuration management for provisioning, which leads to bad results.

[What you want is what you don't: understanding trade-offs in distributed messaging (2015)](http://bravenewgeek.com/what-you-want-is-what-you-dont-understanding-trade-offs-in-distributed-messaging/) - the author makes the point that strong guarantees from lower levels of your distributed infrastructure (ie message queues) are not that good. First, because they impose a big cost on everyone, even if they need it or not. Second, because things like exactly-once delivery are technically impossible to provide without help from the application, and any tool claiming otherwise is exposing you to problems down the road.

[You cannot have exactly-once delivery (2015)](http://bravenewgeek.com/you-cannot-have-exactly-once-delivery/) - linked with the previous article, this is a deeper dive into why precisely "exactly-once" delivery of messages in a distributed system is impossible, and why we must settle for "at most once" or "at least once".

[The first few milliseconds of an HTTPS connection (2009)](http://www.moserware.com/2009/06/first-few-milliseconds-of-https.html) - a bit older but still relevant. There's a lot happening in the TLS/SSL layer to allow HTTPS - much more involved than HTTP itself. For application programmers, it's interesting to know that 3 extra roundtrips are added at the start of the connection, which adds some latency to each new connection.

[Do you really want to be doing this when you're 50? (2012)](http://prog21.dadgum.com/154.html) - part of a series of links about career advice. This one takes a more pessimistic approach, claiming that a job in programming is a high-stress one, which isn't what you want when you're 50. That's a long way off though.

[Do you really want to be making this much money when you're 50 (2012)](http://yosefk.com/blog/do-you-really-want-to-be-making-this-much-money-when-youre-50.html) - an answer to the previous article, arguing that programming is in fact a much lower stress job than medicine/law etc., with a lot of upsides and with comparable pay for high-performers.

[Options vs cash (2017)](https://danluu.com/startup-options/) - startup options are basically worthless in the vast majority of time. Even when they're not, they're as good as working at a bigger company. Sometimes, like when you throw a coin and it lands on its edge, you hit it big. They're also way complex - liquidation preferences, dilution, ISOs etc. seem like a lot of complexity.

[Stock options: a balanced approach (2015)](http://yosefk.com/blog/stock-options-a-balanced-approach.html) - another take on the options vs cash issue. Options are insurance in case the company goes big, rather than actual compensation. Which _does_ make sense. Also, it's a bit of a critique of Dan Luu's assumptions - which most definitely don't apply to everyone in IT for various reasons. From not having the skills to not being in the right place.
