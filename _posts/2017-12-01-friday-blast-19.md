---
published: true
layout: post
date: '2017-12-01 11:20'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #19'
---

[A brief history of select(2) (2016)](https://idea.popcount.org/2016-11-01-a-brief-history-of-select2/) - covers the history of the `select` syscall. Early Unixes were very basic.

[Select is fundamentally broken (2017)](https://idea.popcount.org/2017-01-06-select-is-fundamentally-broken/) - the follow-up to "A brief history of select(2)", this covers why `select` isn't that good, performance wise, and how `poll` and `epoll` try to fix some of it's issues.

[Race condition vs data race (2011)](https://blog.regehr.org/archives/490) - on the topic of things that can go wrong in concurrent programs. Race conditions are any error which occurs under specific timing in the application, whereas data races are explicit cases where two writes write several shared memory locations without any synchronization. They are distinct and one can have one without the other. The neat thing is that data races can be detected automatically, and programs without data races actually have some nice properties.

[Falsehoods programmers believe about [video stuff] (2016)](https://haasn.xyz/posts/2016-12-25-falsehoods-programmers-believe-about-%5Bvideo-stuff%5D.html) - there's a cottage industry of these "falsehoods programmers believe about X" and this article has "X = video stuff". In truth, there's a lot of these things, and some of them are quite scary. Well worth a read if you've ever had to interact with video.

[Everything sysadmin: are you load balancing wrong? (2016)](http://queue.acm.org/detail.cfm?id=3028689) - there's two uses for load balancing - to provide extra capacity or to provide resilience. Your team needs to be clear how you're using yours. For example, if you're using them for extra capacity, you might expect the shards to be at almost full capacity. And when one breaks, the others might not be able to handle the extra traffic. If you think you're doing it for reslliency, you're going to have a bad time.

[Why aren't application downloads routinely done over HTTPS? (2012)](https://security.stackexchange.com/questions/18853/why-arent-application-downloads-routinely-done-over-https) - the bottom line is that you basically only need authenticity, not prevention of MITMs or any other stuff HTTPS provides. Furthermore, due to the way downloads are done (with mirrors etc), you need some extra infrastructure on top of that as well.

[Little's Law (2017) #own](http://horia141.com/littles-law.html) - this is one of my own from the last week. It's about a nice result from queuing theory with many applications in building distributed applications.
