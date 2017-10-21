---
published: true
layout: post
date: '2017-10-20 10:30'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #14'
---

[What is the effect of ordering if...else statements by probability (2017)](https://stackoverflow.com/questions/46833310/what-is-the-effect-of-ordering-if-else-if-statements-by-probability) - both theoretically and empirically, ordering the branches in decreasing probability of being taken results in better performance. Granted, you're only likely to see it in microbenchmarks. But it's still interesting, cause a "readability" best practice I use is have the least-likely to be taken cases in functions and loops first. Since they're most likely error handlers rather than real code, and leave the bulk of the method for last.

[How developers can best negotiate their salaries (2017)](https://stackoverflow.blog/2017/10/16/developers-can-best-negotiate-salary/) - a nicely written piece by my colleague [Nick Larsen](https://twitter.com/fody?lang=en) on some "technical" aspects of salary negotiations. Namely pricing yourself relative to the market. Besides the really nice prose, I also liked the fact that it didn't rely on psychological or "negotiation theory" tools. Which while useful, they might be hard to master for somebody who negociates once or twice a year.

[Why Trello failed to build a billon dollar business (2017)](https://blog.usejournal.com/why-trello-failed-to-build-a-1-billion-business-e1579511d5dc) - mostly because they did not _try_ or did not succeed in becoming central to people's workflows. Which meant specialization for various verticals and integration with all the other SMB & Enterprise tools (GitHub, Slack, Jira etc.). After a while, many other tools copied their nice UI and they were left with tne still-great-but-not-super acquisition by Atlassian.

[State of the art JavaScript 2016 (2016)](https://medium.com/javascript-and-opinions/state-of-the-art-javascript-in-2016-ab67fc68eb0b) - SPAs, React, Redux, Webpack, ES6 or TypeScript if you must, NPM, Mocha+Chai+Sinon, Lodash, fetch. A lot of things, but each one is small by itself. The list has stayed mostly the same to 2017, with Vue.js as a contender for React.

[Application architectures with persistent storage (2014)](http://firstclassthoughts.co.uk/Articles/Design/ApplicationArchitecturesWithPersistentStorage.html) - a nice history and overview of how people organize their applications around databases. Covers things from "all applications use one central database" to "each application has several datastores specialized for different tasks" (ie microservices). Careful that there's a mismatch between how to organize things at the "physical level" of services and their dependent DBs, and "logical level" of how to organize SaaS-like customers.

[Why are Facebook, Twitter, Digg so hard to scale? (2009)](http://highscalability.com/blog/2009/10/13/why-are-facebook-digg-and-twitter-so-hard-to-scale.html) - you can tell this is an old article by putting Digg in the same class as Facebook and Twitter. The reason is that the datasets for one user is dependent on the dataset for the other users in a realtime fashion. So the usual tricks of horizontal scaling don't work. Facebook took the approach of polling each of the friends to build a response, and thus moving the load to "read time", whereas Twitter took the approach of sending tweets to followers' inboxes, and thus moving the load to "write time".

[Introduction to release engineering (2016)](https://www.oreilly.com/ideas/introduction-to-release-engineering) - very large companies like Google, Microsoft, Facebook etc. have a whole host of developers working on specific aspects of the "infrastructure". Some work on testing tools, others on build tools, and yet others on "release tools". This article is about the latter, and the way to do it. It's good advice for most dev teams. Though most won't have the bandwidth to build their own, and will have to work by process and convention to achieve some of the things the tools at Google would enforce.

[A decade of container control at Google (2016)](https://www.nextplatform.com/2016/03/22/decade-container-control-google/) - a bit of the history of containers inside Google and the evolution from their early cluster management software to Kubernetes.