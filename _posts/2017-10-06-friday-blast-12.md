---
published: true
layout: post
date: '2017-10-06 11:30'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #12'
---

[Clocks for software engineers (2017)](http://zipcpu.com/blog/2017/09/18/clocks-for-sw-engineers.html) - hardware design is very different from software design. And it starts from the very basic concept of the _clock_, which is the periodic and square-ish signal which synchronizes all the other components of the design. There's a whole bunch of hardware design tips on the website as well.

[Building ReplicatedLog: high-performance replicated log service (2015)](https://blog.twitter.com/engineering/en_us/topics/infrastructure/2015/building-distributedlog-twitter-s-high-performance-replicated-log-servic.html) - a quick overview of Twitter's ReplicatedLog. The service is similar to Kafka, but with different tradeoff and a lower-level interface, upon which their pub/sub systems, databases etc. can build. Having lower-level systems with good abstractions and performance available, makes building other distributed systems much simpler. Indeed, their Manhattan distributed database is built atop this. Other systems like BigTable depend upon a reliable system like the Google File System, hwhich makes their design much simpler. In contrast, something like Amazon's Dynamo has to take care of everything itself, leading to a much more complex design.

[Stacking up the next platform (2015)](https://www.nextplatform.com/2015/10/16/stacking-up-a-modern-platform/) - a description of what a "platform" should contain and provide from it's users, with a decidedly Google/Facebook/Twitter-like approach. Things like container infrastructure (runtime management and registries), build systems, logging, load balancers etc. The article is from 2015, but it's been quite predictive of what has happened in the meantime. The only thing not covered is the "rise" of Function-As-A-Service / serverless.

[Floating point visually explained (2017)](http://fabiensanglard.net/floating_point_visually_explained/) - I got a lot of bang out of this article. Like the author I struggled with the definition of floating point. This article cleared a lot of issues for me. Basically, the exponent part of the FP number selects one of a range of numbers, while the mantissa selects one element from that range. The ranges are exponentially increasing, so in each range the resolution decreases. Read on for more details and graphics.

[Essential facts about floating point calculations (2016)](https://mortoray.com/2015/07/06/essential-facts-about-floating-point-calculations/) - much easier to understand in light of the previous article. The core idea is that FP numbers are not reals, so many of our intuitions about them are wrong. Also, the hardware implementation might bite us. The most glaring example would be that both $$x == y$$ and $$x != y$$ are false at the same time, because x86/x64 machines use $$80$$ bit precision FP units.
