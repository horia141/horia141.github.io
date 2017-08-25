---
published: true
title: "Friday Blast #7"
layout: post
date: 2017-08-25 10:39
categories: post
tags: friday_blast links
comments: true
math: true
---

A shorter week this week. Didn't get that much reading on account of spending most of my reading time on Designing Data Intensive Applications.

[A history of branch prediction from 1500000 BC to 1995 (2017)](https://danluu.com/branch-prediction/) - branch prediction algorithms are used by CPUs to, you guessed it, predict which branch of an `if`, `for` or `while` condition is going to be taken. It's of vital importance to get this right in deeply pipelined CPUs[1], because the cost of a mis-predict is a discarding of all the processing done on the current instruction. This article is an introduction and overview up to the year 1995. Very interesting none-the-less, especially since things started repeating themselves as progress was made, as is oft the case.

[What next (2017)](http://graydon2.dreamwidth.org/253769.html) - this deals with what future ideas from programming language research the author would like commercial programming languages to start using. Modules and error handling seem to be the biggest asks. Which I found interesting, cause I thought modules and error handling _were_ solved to a large degree in modern languages. Turns out that's not the case and there's a huge body of work trying to get them _right_. From the list I'd love to see effects systems and extended static checking turn up in more programming languages. Much of the stuff in [Raynor](https://github.com/horia141/raynor) could be expressed as static checks for example.

[Distributed commit log - application techniques for transaction processing (2016) #talk](https://www.youtube.com/watch?v=X2g0FFOV2e0&t=9s) - I had higher hopes for this video, but it's still a good watch. There's not so much talk about how to structure applications around distributed logs, but rather how to go about making things work within the limitations of [Amazon Kinesis](https://aws.amazon.com/kinesis/), and, to a certain extent [Apache Kafka](https://kafka.apache.org/).

[How to get started with technical public speaking (2017) #talk](http://www.hanselman.com/blog/VIDEOHowToGetStartedWithTechnicalPublicSpeaking.aspx) - technical public speaking is something I want to get into at some point. This talk gives some very solid pointers on how to give such a talk, as well as any presentation. There's a couple of hints as to how to get started - speak in small groups, inside your company or at colleges and then grow from there.

---
[1] So, in all of them?
