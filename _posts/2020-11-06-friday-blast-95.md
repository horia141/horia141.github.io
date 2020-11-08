---
published: true
layout: post
date: '2020-11-06 07:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #95'
---
[Productionizing Spark streaming applications (2019)](https://blog.clairvoyantsoft.com/productionalizing-spark-streaming-applications-4d1c8711c7b0?gi=5cae7fb77bd1) - we
had to use Spark streaming for a project at [Bolt](https://bolt.eu), and this guide proved mighty useful for
getting us in the right headspace for tackling the problem.

[Asynchronous computing at Facebook (2020)](https://engineering.fb.com/2020/08/17/production-engineering/async/) - an
overview of Facebook's complex system for handling "notifications" and "notification-like events". A message queue
in a way. As a side-note, I've noticed that systems that are essentially message queues (chat systems, notification
systems, etc.) don't ever seem to be implemented as an infrastructure-level message queue (Kafka, SQS, etc.), but
rather in a traditional fashion (mixes of databases, queues, caches, servers, etc.).

[Big data architecture patterns (2014)](https://www.youtube.com/watch?v=-N9i-YXoQBE&feature=youtu.be) - a short
overview of how a modern-ish data infrastructure layer looks like - data lakes, ML systems, etc. included.

[Mutation testing - a tale of two suites (2020)](https://codeascraft.com/2020/08/17/mutation-testing-a-tale-of-two-suites/) - about
how Esty used _mutation testing_ to migrate from one test framework to another. It was the first time I heard
of mutation testing (with this definition at least - but the name sounds familiar). It is a test for tests essentially.
It applies a batter of mutations to the code base, and runs the test suite on it. Ideally the test suite should fail
in the appropriate manner. Quite an interesting and powerful code quality tool - a step above just having tests, and
in the realm of code coverage tooling, fuzzing, etc.

[An introduction to CQRS and Event Sourcing patterns (2017)](https://www.youtube.com/watch?v=9a1PqwFrMP0&feature=youtu.be) - again
an intro talk on these two more advanced architecture patterns.
