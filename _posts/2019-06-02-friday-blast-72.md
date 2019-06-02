---
published: true
layout: post
date: '2019-06-02 07:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #72'
---
[Replicated data consistency explained through baseball (2019)](https://mwhittaker.github.io/consistency_in_distributed_systems/1_baseball.html) - a first part of a series dedicated to _consistency in distributed systems_. This one prepares the ground and then reviews the article of the same name. Granted, I don't know the baseball rules, but I picked up enough to get something decent out of this.

[When Google Wave crashed and the tech press burned (2019)](https://500ish.com/when-google-wave-crashed-and-the-tech-press-burned-84cc99eb518a) - about how the tech press and society at large has become more cynical about consumer technology. It's easy to miss that _this stuff_ is just 20 years old. We've had computers for 70-80 years and networks of them for about 50. But it's only with the personal computer and the web that they've started impacting society at large in a _grand way_. So we're in uncharted waters, and they're quite perilous to boot.

[Von Neumann's critique of automata theory and logic in computer science (1947)](https://www.yodaiken.com/2019/02/20/von-neumanns-critique-of-automata-theory-and-logic-in-computer-science/) - interesting read. Interesting that such things crop up wrt distributed systems, but we've made single computers so reliable as to not make it required to think about hardware failures except as catastrophic.

[Serverless pitfalls - issues with running a startup on AWS Lambda (2019)](https://medium.com/@emaildelivery/serverless-pitfalls-issues-you-may-encounter-running-a-start-up-on-aws-lambda-f242b404f41c) - from the "why would you do that?" series. Now, it isn't a bad idea to use serverless for some things. But for everything like the authors do? Not there yet - and perhaps we never will. In the end they settled on a hybrid approach with some stuff on Lambda and some latency sensitive stuff in regular old VMs.

[Serverless computing - one step forward, two steps back (2019)](https://blog.acolyer.org/2019/01/14/serverless-computing-one-step-forward-two-steps-back/) - a morning paper review of a paper by Hellerstein (of database fame) critiquing serverless computing. Their idea is not to bash on serverless but to rather incite folks to build _better_ offerings here.
