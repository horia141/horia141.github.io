---
published: true
layout: post
date: '2018-01-12 20:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #23'
---

[Threads cannot be implemented as a library (2004) #pdf](http://www.hpl.hp.com/techreports/2004/HPL-2004-209.pdf) - the main point is that for superior concurrency support, the language needs to step in. It's not enough to rely on a library such as `pthreads`. The reasoning is both performance related - such libraries want every synchronization to go through them, and don't really say anything about shared variables which are used without library provided synchronization. However, modern processors offer some primitives outside of locking - atomic operations, fences etc. which _are_ required for best performance, but which can't be expressed correctly if the compiler does reorderings or other optimizations. It is also safety related. Some optimizations, which might be unaware of the special behavior of `pthreads` functions _may_ yield race conditions or other unexpected behaviors. This works comes in the wake of the seminal Java Memory Model, but addresses C/C++ and other low-level languages (Ada?). It all culminated with C and C++ having _memory models_ in the later revisions.

[I'm harvesting credit card numbers and passwords from your site. Here's how (2017)](https://hackernoon.com/im-harvesting-credit-card-numbers-and-passwords-from-your-site-here-s-how-9a8cb347c5b5) - our reliance on third-party libraries is both a blessing and a curse. If we have an un-audited dependency (or dependency of dependency) which can execute in a sensitive context then that can be used to steal confidential information. The author proposes a crafty example of how this might go about with NPM for frontend code, where there's a particular abundance of small and not-very-well-audited packages a project might depend on. I feel some of the reason this is, is the fact that JS is not _batteries included_. So we need to have things like a [`left pad`](https://www.theregister.co.uk/2016/03/23/npm_left_pad_chaos/) module.

[SQL keys in depth (2017)](https://begriffs.com/posts/2018-01-01-sql-keys-in-depth.html) - a data modeling overview of SQL keys. Didn't realize primary keys were more of an implementation artifact than anything else. There's a lot of material about natural vs artificial keys, and how to go about working with surrogate keys. Well worth the read.

[Memory bandwidth (2017)](https://fgiesen.wordpress.com/2017/04/11/memory-bandwidth/) - intuitions about why _memory is such a problem_ for systems. In terms of _bytes accessible per clock cycle_, we've gone from 4 bytes/instruction with the MOS 6502 to 1 byte/instruction with a recent Core i7. For SIMT modes or GPUs things are even more drastic. So while in absolute terms memory capacity and bandwidth have gone up, relative to how many instructions a processor can execute, things were made worse.

[Modes, medians and means - a unifying perspective (2013)](http://www.johnmyleswhite.com/notebook/2013/03/22/modes-medians-and-means-an-unifying-perspective/) - turns out that the mode, median and means are all expected value of three discrepancy measures for a distribution, which look very much the same.

[Do you know how much your computer can do in a second (2017)](http://computers-are-fast.github.io/) - a lot of some things, and very few of other things. Most of the code is in Python, but even with that, you get to see things like - sequential memory access is fast while random one is slow, or file IO is slow, but network access over the Internet is even slower. One can do 1-2 requests per second for example - the lowest value from the examples. Though there's scope for a lot of async IO there to increase throughput. The best part is this is given as a quiz.
