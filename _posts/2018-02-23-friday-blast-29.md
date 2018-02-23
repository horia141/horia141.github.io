---
published: true
layout: post
date: '2018-02-23 14:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #29'
---

[The ultimate guide to progressive web applications (2017)](https://dzone.com/articles/the-ultimate-guide-to-progressive-web-applications) - one of the better developments in the recent tech space has been a resurgence of websites/SPAs under the guise of progressive web applications as viable contenders to native applications. Well worth a read as an introduction, but not that many technical details. 

[Hot to structure permissions in a SaaS app (2018)](https://heapanalytics.com/blog/engineering/structure-permissions-saas-app) - a nice article from Heap Analytics on role base access control. There's resources and actions which can be taken on a resource, and more or less each one requires a _permissions_. Then there's roles which are groupings of permissions. Finally, there's users, who are assigned various roles. A bunch of other best practices and links to other resources are present as well.

[12 best practices for user account, authorization and password management (2018)](https://cloudplatform.googleblog.com/2018/01/12-best-practices-for-user-account.html) - tied a little bit with the previous article. This is a topic I've covered a bunch of times in this series of links. The perenial advice remains - don't roll your own.

[Cache coherency primer (2014)](https://fgiesen.wordpress.com/2014/07/07/cache-coherency/) - going lower level with this article. It's a presentation of cache coherency for single processor and multi-core/multi-processor systems. It starts of with the general invariants and operating mode of caches, and goes on to present what happens in multi-core systems with the MESI cache coherency protocol.

[Atomic operations and contention (2014)](https://fgiesen.wordpress.com/2014/08/18/atomics-and-contention/) - again a lower level article. Presents how atomic operations are implemented in terms of the memory and caches. Covers a little bit the separation of atomics and memory barriers I've mentioned before on other Friday Blast posts and why both are needed for different reasons.
