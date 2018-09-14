---
published: true
layout: post
date: '2018-09-14 07:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #53'
---
[Notes on structure concurrency or go statement considered harmful (2018)](https://vorpus.org/blog/notes-on-structured-concurrency-or-go-statement-considered-harmful/) - making the case that the `go` statement (or `async/await` or the equivalent functions from other languages) is just as good for concurrent programming as `goto` was for the early programming of the 50s and 60s. Which is not that good. The idea of nurseries, which the author proposes _does_ look nice, though without language support in the form of nicer syntax I don't really see it catch on.

[Scaling a high-traffic rate limiting stack with Redis cluster (2018)](https://brandur.org/redis-cluster) - A study of how Stripe improved their handling of rate limiting. Scary stuff that there was _one single Redis machine doing all this_ (granted, with a bunch of secondaries). The discussion on "ambient" error rate is super as well - one of the big differences between small scale and large scale systems.

[The tectonics of the web (2018)](https://frontendian.co/the-tectonics-of-the-web) - Rundown of the IETF, W3C and ECMA - three standards organizations which more or less define what's happening on the web and Internet to a larger extent.

[The Web I want (2018)](https://dev.to/quii/the-web-i-want-43o) - less JS and more HTML&CSS. When it's the case. I think the "think of all the places with bad internet"/"thing of the batteries" argument is the best to sway folks to keep things simple.

[Developing real-time web applications with server-sent events (2018)](https://auth0.com/blog/developing-real-time-web-applications-with-server-sent-events/) - SSEs are a newish API for folks to use. They're a specialization of the bidirectional communication that web sockets allow. Only the server is allowed to send data, in response to a client request. So they're duals of the regular "request-response" approach which is the standard. The article does a thorough job of exploring them and the edge cases they have. Especially those around lost connections.
