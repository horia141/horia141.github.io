---
published: true
layout: post
date: '2019-02-01 07:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #59'
---
[Azure Cosmos DB (2018)](http://muratbuffalo.blogspot.com/2018/08/azure-cosmos-db.html) - Murat was a CS professor who's blog I was following for some time. Recently he's made the jump to industry, at least for a Sabbatical, working on Microsoft's Cosmos DB. I had some vague knowledge of it, as this sort of Spanner / Cloud Data Store type thing. But it seems it's _so much more_ than that. Or at least it attempts to. It's wants to basically be a all-in-one database, with OLAP and OLTP support, distributed by default, planet scale geo-distribution by default and with all sorts of APIs for accessing it: SQL, Mongo etc. Probably fun to build against, but not so fun to _depend on it_, cause it's unlikely anybody will be able to match it soon. Still, interesting read and the first of many detailing his work on the system.

[The joys of circuit breaking (2018)](https://medium.com/zendesk-engineering/the-joys-of-circuit-breaking-ee6584acd687) - circuit breakers are a fundamental pattern when building distributed systems (at least the RPC based variety). They're simple enough - if a service is consistent in failure, mark it as such as a caller and fail fast later. However, when combined with retries and rate-limiting the interactions are subtle and open up the avenue for interesting and catastrophic failures. Like the team at ZenDesk found out.

[The many faces of consistency (2018)](http://muratbuffalo.blogspot.com/2018/08/the-many-faces-of-consistency.html) - a review of [this](https://pdfs.semanticscholar.org/8d67/a8f90586e3c074a60a871a210785ee61c43e.pdf) paper. Both easy reads. The case is that consistency is kind of an overloaded term in the _systems_ community. And the authors attempt to break it down into _operational_ and _state_ consistency, while giving examples of how the traditional notions (sequential consistency, linearizability etc) map to them. Good read. This is a field which is constantly evolving, so the terms are still fuzzy.

[E-commerce at scale: inside Shopify's tech stack (2018)](https://engineering.shopify.com/blogs/engineering/e-commerce-at-scale-inside-shopifys-tech-stack) - interesting read about Shopify's architecture. The most interesting thing is their approach to sharding. Basically the whole setup is sharded - not just DBs or webservers, but caches, Redises etc. There's a whole bunch of identical systems running inside Shopify, all of them handling various shops independently. This is quite interesting and a mix between the traditional "one-setup-per-client" some shops use, and "everyting-together" other SaaS companies use. Curious how they deal with centralised services for logging, monitoring etc. The biggest downside I can see is a more complex release process. You have to do N database migrations instead of one big one.
