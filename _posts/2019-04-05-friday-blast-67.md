---
published: true
layout: post
date: '2019-04-05 07:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #67'
---
[Everything you need to know about networking on AWS (2018)](https://grahamlyons.com/article/everything-you-need-to-know-about-networking-on-aws) - fun and bitesized read about how AWS organises "networks". Since you're dealing with IaaS (among many other things), you can set things up at the network level as well. And even if you only want to deal with managed services, you'll be hit by this. I'm tangentially involved with this stuff, so a refresher is good. Especially one which shows "how things are in real life usually", like this one.

[OAuth 2.0 and the road to hell (2012)](https://hueniverse.com/oauth-2-0-and-the-road-to-hell-8eec45921529) - I've mostly interacted with OAuth through well-defined interfaces, like the Auth0 one. Even then it wasn't 100% nice. This is a rant / farewell letter to OAuth 2.0 by one of the authors of the specification. A lot of stuff about _what went wrong_ - design by committee mostly.

[User IDs probably shouldn't be passed around as ints (2018)](https://rachelbythebay.com/w/2018/04/27/uid/) - the logic here is straightforward. Users (or entities) in general should have some notion of identity separate from the primary key of the database system used to store them. This helps with all sorts of things: sharding, security (not allowing folks to guess user ids, especially of really early users), obscurity (not giving insights to competitors about the number of users, widgets etc managed by the system), referencing from external systems, migrations etc. It all comes with some extra cost though: storage space, the need to write more careful code etc.

[Missing the point about microservices - it's about testing and deploying independently (2018)](https://erikbern.com/2018/06/04/missing-the-point-about-microservices.html) - the title says it all. The "questionable reasons" section is pretty golden. It tackles some of the _obvious strengths_ of the approach which I'd also _not_ encountered in real life and had an inkling were quite bogus - writing in different languages, hard independence as a code separation tool, independent scaling between systems etc.
