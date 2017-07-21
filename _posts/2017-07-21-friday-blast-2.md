---
published: true
title: "Friday Blast #2"
layout: post
date: 2017-07-21 12:22
categories: post
tags: friday_blast links
comments: true
math: false
---

In this post I've begun putting the year next to the link. The bias will be towards more recent articles, of course. But sometimes it's useful to know the context of a piece to be able to judge its content/advice.

[Ten common database design mistakes (2007)](https://www.red-gate.com/simple-talk/sql/database-administration/ten-common-database-design-mistakes/) - funnily enough, many of the mistakes are around the development processes around using a database. Testing, documentation, coding standards etc. Which would still hold if we'd be talking about software development in general. The only bit of advice that hasn't survived the test of time is the one about using stored procedures. Depending on who you ask, stored procedures are anywhere between a necessary evil or an antipattern.

[DNS: The good parts (2013)](https://www.petekeen.net/dns-the-good-parts) -  a quick overview of DNS from an application programmer's perspective. The title is an ode to [JavaScript - The Good Parts](http://shop.oreilly.com/product/9780596517748.do), though I imagine there's more goodness to DNS than a 10 minute read.

[Intro to Ad Tech (2017)](https://dev.adzerk.com/docs/glossary) - part of Adzerk's documentation, this is a high-level overview of the business side of AdTech. Basic stuff programmers in the field should know, as well as useful info for anybody curious.

[Backends for Frontends (2015)](http://samnewman.io/patterns/architectural/bff/) - the thing I like most about this article is that it gives a name to a pattern I've encountered several times before. A backend for a frontend (BFF) is a service heavily tailored to providing data for a specific frontend. While other services are APIs and must be client-agnostic and "generic", the BFF is coupled to the client(s) it serves, and should even be developed by the client team. I've some opinions of my own in [On backends for frontends](http://horia141.com/on-bffs.html).

[Stream all the things (2017) #talk](https://www.youtube.com/watch?v=Hjae0Cw9oew) - a talk about recent streaming approaches in building the _data infrastructure_ for companies. It's also a plug for Kafka, but then again Kafka seems to be quite the nice piece of technology, so I don't mind that much. The gist is that every event which happens in an organization - from pageview to widget being produced on the factory floor - should be placed in a centeralized streaming log, out of which every other process works.

[International box-sizing awareness day (2014)](https://css-tricks.com/international-box-sizing-awareness-day/) and [Inheriting box-sizing probably slightly better best-practice (2014)](https://css-tricks.com/inheriting-box-sizing-probably-slightly-better-best-practice/) - the takeaway is that you should use `box-sizing: border-box` as the default for all your elements, since it makes everything much better.

[Autoprefixer: a postprocessor for dealing with vendor prefixes in the best possible way (2013)](https://css-tricks.com/autoprefixer/) - again, the takeaway is that you should use [Autoprefixer](https://github.com/postcss/autoprefixer) as part of your frontend build chain, since it does CSS vendor prefixing for you _auto_-matically and with a lot more knowledge.

[UUID vs BIGSSERIAL for primary keys (2015)](http://thebuild.com/blog/2015/10/08/uuid-vs-bigserial-for-primary-keys/) and [UUID or GUID as primary keys? Be careful! (2017)](https://tomharrisonjr.com/uuid-or-guid-as-primary-keys-be-careful-7b2aa3dcb439) - two articles dealing with the pros and cons of UUIDs as primary keys.
