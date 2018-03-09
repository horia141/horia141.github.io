---
published: true
layout: post
date: '2018-03-09 15:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #31'
---

[A practical introduction to container terminology (2018)](https://developers.redhat.com/blog/2018/02/22/container-terminology-practical-introduction/) - if you've ever worked with Docker or other container tech, you've probably been a bit confused by all the names - container, repository, registry, image etc. There's a lot to unpack and a lot of people using one name when they mean another. This is a long-ish presentation & glossary of container terms from RedHat.

[What I did wrong as a CTO (2018)](https://geowarin.github.io/what-i-did-wrong-as-a-cto/) - catchy title. This is mostly about technology choices and how those played out. I think the key takeway is - the choices are sticky and stuff which is too experimental will bite you. A breakdown of organizational and people issues would have been more interesting I think.

---

The following series of 4 articles describes Uber's `Schemaless` system - a NoSQL-like database with some very neat capabilities - multiple indices, triggers and an interesting melange of strong & weak/eventual consistency guarantees. All built on top of MySQL. Which is something of a cottage industry for MySQL - DynamoDB is also built atop it.

[Project Mezzanine: the great migration (2015)](http://eng.uber.com/mezzanine-migration/) - this part describes the problem they're trying to solve and the current solution they have, as well as the migration process to Schemaless.

[Designing Schemaless, Uber Engineering's scalable datastore using MySQL (2016)](https://eng.uber.com/schemaless-part-one/) - this one goes into the guts and architecture of the system. It also provides reasons for why other options were not good enough. Otherwise the system looks very much like BigTable/HBase with some immutability thrown in.

[The architecture of Schemaless, Uber Engineering's trip datastore using MySQL (2016)](https://eng.uber.com/schemaless-part-two/) - this one speaks about the distributed systems aspects of the database. What sort of nodes there are, how clients speak to them etc.

[Using triggers on Schemaless, Uber Engineering's trip datastore using MySQL (2016)](https://eng.uber.com/schemaless-part-three/) - an overview of the triggering mechanisms. This is very similar to how something like Kafka works. The immutable key-values form a sharded log. The DB maintains read indices for clients (on the idea that there aren't that many of them), and just notifies them via an RPC when there's a change. It's up to them and the Schemaless framework code inside the clients to read the data and process it. Idempotency is a big plus here.

[Code migration in production: rewriting the sharing layer of Uber's Schemaless datastore (2018)](https://eng.uber.com/schemaless-rewrite/) - two years have gone by and the system has grown. This isn't an architecture overview, as much as description of how they went about replacing the worker node's Python code with much more scalable Go. The hard part, as in other migrations, is ensuring the two codepaths return exactly the same results.
