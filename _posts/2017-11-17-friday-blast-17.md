---
published: true
layout: post
date: '2017-11-17 10:30'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #17'
---

[Ask HN: What language agnostic programming books should I read? (2017)](https://news.ycombinator.com/item?id=14486657) - A Hacker News discussion with loads of good titles. I'd go so far as to say that _most_ good tech books are independent of the technology itself and present timeless bits of knowledge.

[Debugging PostgreSQL performance the hard way (2016)](https://www.justwatch.com/blog/post/debugging-postgresql-performance-the-hard-way/) - good advice for any SQl debugging session. Start with the "obvious" stuff like system-level metrics and work your way down to individual slow queries.

[Robust user interfaces with finite state machines (2017)](https://css-tricks.com/robust-react-user-interfaces-with-finite-state-machines/) - this is really a wonderful article and a good example of how knowing a little bit of theory can make building things _that_ much easier. The idea is that you should be explicit about the state structure of your UI, since it'll result in easier to reason code. I can attest from my own experience that that's the case. Modern web frameworks like Angular, Vue and React as well as the Android and iOS platforms make thinking about your UI in these terms much easier than the "old" days of the web or old-timey Win32 programming.

[Software 2.0 (2017)](https://medium.com/@karpathy/software-2-0-a64152b37c35) - an article about machine learning and neural networks in particular and where they belong in the grand scheme of software development. I think naming them as software 2.0 is a much too early call. Perhaps software 1.1 or 1.5. Right now they're just good tools for particular subproblems such as image recognition or audio synthesis. But it's going to be a long way 'till you can write a text processor through a neural network.

[Hash chain (2017)](https://en.m.wikipedia.org/wiki/Hash_chain) - a wikipedia entry for a neat idea for authentication without actually sending the password on the wire for each attempt. The gist is that the client and server agree on a common count $$k$$ and the server stores the password hashed $$k$$ times. For the first auth the client sends the password hashed $$k-1$$ times, and the server computes the $$k$$th one and compares it with its own value to allow auth or not. On the next attempt the count is decremented by $$1$$, with the server storing the hash it has received from the client for later user. No password is sent over the wire, and if anybody easedrops on what _is_ sent, they'll have no use for it since it won't be used a second time. The client need not store $$k$$, since it can receive it from the server at the start of the auth session, so there's no complex state to synchronize.

[Statistical mistakes and how to avoid them (2016)](http://www.cs.cornell.edu/~asampson/blog/statsmistakes.html) - this is more a call to use statistical tools such as scalar descriptive stats and tests when reporting results of any kind in computer science, than anything else. You _should_ do it though.

