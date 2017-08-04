---
published: true
title: "Friday Blast #4"
layout: post
date: 2017-08-04 10:39
categories: post
tags: friday_blast links
comments: true
math: false
---

There's a good mix of recent and older articles this week. I'd say they veer towards being longer this week, but they're also more essay-like, so they should be easier to grok.

[Flash is dead: what technologies might be next? (2017)](https://stackoverflow.blog/2017/08/01/flash-dead-technologies-might-next/?cb=1) - a look into how questions on StackOverflow evolved over time for Flash, and what other technologies might show the same behaviour. jQuery and Ruby on Rails are _contenders_ here.

[How flexbox works - explained with big, colorful, animated gifs (2017)](https://medium.freecodecamp.org/an-animated-guide-to-flexbox-d280cf6afc35) - what the title says. If you haven't used flexbox in your frontend projects you definitely should. It make things so much simpler. And it has almost universal support.

[Docker security best practices (2017)](https://blog.sqreen.io/docker-security/?utm_source=cronweekly.com) - I was expecting the vanilla advice of not running things as root inside the container etc. But this goes into higher-level approaches like image authenticity and using Docker Bench Security. The takeway here is that while Docker removes some security issues, it adds a lot of its own as well.

[History of the browser user-agent string (2010)](http://webaim.org/blog/user-agent-string-history/) - it's always fun to be reminded of how insane user agent strings are. Doubly so when it's in the faux biblical style employed in this article.

[The JavaScript event loop: explained (2013)](https://blog.carbonfive.com/2013/10/27/the-javascript-event-loop-explained/) - quick intro into the event loop of JavaScript. While there's more to it than this overview, it is nonetheless useful for anybody coming from a more traditional background. Fun fact - [Tcl](https://www.tcl.tk/) has a similar concept, and it's author has been involved in popularizing event loops as alternatives to traditional concurrent programming with threads. It took a while, but things like `async/await`, event driven web servers etc. follow from that work.

[Running 10 Million PostgreSQL indexes in production (and counting) (2017)](https://heap.engineering/running-10-million-postgresql-indexes-in-production/) - a tremendous article about a really insane usage of PostgreSQL at [Heap](https://heap.engineering/). For every type of event captured they define a partial index - an index with a `where` clause more or less. These are created in an ad-hoc fashion, as users define and use events. What I liked about this was that they managed to map a business concept so neatly to a feature of the database.

[The Vietnam of computer science (2006)](http://blogs.tedneward.com/post/the-vietnam-of-computer-science/) - an article about ORMs and their woes. There's also a rather detailed overview of the Vietnam War and how the US suffered from it, which is an interesting read in itself. If you're left confused about what to use after reading this article, try an micro-ORM like [Dapper](https://stackexchange.github.io/Dapper/) or [knex.js](http://knexjs.org/), which provide all the useful bits of ORMs, but don't try to take over too much of the database. Libraries, not frameworks.

[A real-time database survey: the architecture of Meteor, RethingDB, Parse & Firebase (2016)](https://medium.baqend.com/real-time-databases-explained-why-meteor-rethinkdb-parse-and-firebase-dont-scale-822ff87d2f87) - a really interesting read from Wolfram Winegarth, who works at [Baqend](https://www.baqend.com/), which is a BaaS provider. There's links to the classic [NoSQL databses: a survey and decision guidance](https://medium.baqend.com/nosql-databases-a-survey-and-decision-guidance-ea7823a822d) and [Scalable stream processing: a survey of Storm, Samza, Spark and Flink](https://medium.baqend.com/real-time-stream-processors-a-survey-and-decision-guidance-6d248f692056). The gist is that real-time queries, that is, queries which produce a stream of results and capture changes to the database as they happen, are nice and good to have. But they're difficul to get to work in a scalable way, and most solutions either don't support a lot of queries, or the system doesn't scale with write throughput for these queries. It's also a marketing pieces, so obviously, Baquend does do all these things right.