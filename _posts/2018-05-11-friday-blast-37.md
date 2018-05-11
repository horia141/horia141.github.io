---
published: true
layout: post
date: '2018-05-11 07:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #37'
---

Today's friday links are all over the map. Can't have all of them be themed.

[The various kind sof IO - blocking, non-blocking, multiplexed and async (2018)](https://www.rubberducking.com/2018/05/the-various-kinds-of-io-blocking-non.html) - the core insight is that asynchronous I/O is independent of multithreading. Other than that, it's pretty systematic in covering the various ways a program can deal with I/O from a time and work perspective.

[Is Docker the new Git? (2018)](https://www.codingblocks.net/programming/is-docker-the-new-git/) - the author makes the point that there's a bunch of technologies which win cause they're good or good enough for most cases. Even if you don't have the problems they're solving exactly, or if you're invested into an alternative, it might make sense to adopt them. Git was one such tool, Java another, the Cloud a third and Docker might be a good candidate.

[More environments will not make things easier (2018)](https://bravenewgeek.com/more-environments-will-not-make-things-easier/) - Links to Tyler Treat's blog are always a treat. Pun intended. But they usually deal with distributed systems lower-level issues. Today's link is about architecture concerns and how microservices are hard and some strategies to dealing with them at the integration level. I like the idea of consume-driven contract testing, as well as the realization that what's keeping many of these things running are good teams rather than just practice X or Y.

[Event sourcing made simple (2018)](https://kickstarter.engineering/event-sourcing-made-simple-4a2625113224) - Event Sourcing is an intriguing approach to the architecture of larger applications. Sadly, it does require discipline and a host of infrastructure to make them work. Which might not be worth it for smaller projects. But the article here presents just the approach to work in such cases. It's pretty interesting, but it's mostly a retrofitting of ES concepts - events tables and aggregates being written by the same transaction from a single request handler, a tighter code coupling etc. It's something I've actually _used_ in projects to a certain extent. So not so exotic after all.

[Conceptual compression means beginner don't need to know SQL - hallelujah (2018)](https://m.signalvnoise.com/conceptual-compression-means-beginners-dont-need-to-know-sql-hallelujah-661c1eaed983?source=rss----668e14b18fb1---4) - a well-written DHH article on how we're advancing as a field, and things which were _essential knowledge_ yesterday, become today's arcana. The example is on SQL, but CPU and memory structures, assembler, OS internals etc. are all on the spectrum somewhere. I think the killer takeway here is the idea that we're doing all these abstractions with the goal of making it easy for one developer or a small group of them to fully build an application. And I think that's a very powerful thing. Cause it's no fun when you need 10+ types of developers to build something.
