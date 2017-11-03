---
published: true
layout: post
date: '2017-11-03 10:30'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #15'
---

[Practical advice for analysis of large, complex data sets (2016)](http://www.unofficialgoogledatascience.com/2016/10/practical-advice-for-analysis-of-large.html?m=1) - advice from the Google data scientists working on ads. Now, I think this is good advice for any software engineer working on complex projects. Many projects will involve analysis of large data sets, running experiments and A/B tests etc.

[Falsehoods programmers believe about networks (2012)](http://blog.erratasec.com/2012/06/falsehoods-programmers-believe-about.html#.WA3SA5N95By) - there's a small cottage history of these "falsehoods" articles. This time, networks are the target.

[What every systems programmer should know about lockless concurrency (2017)](https://assets.bitbashing.io/papers/lockless.pdf) - the largest chunk of this article is about the memory model presented by modern CPUs and how that translates to programming languages. In turn, this allows the implementation of lockless algorithms or data structures by using many of the tools used to actually implement locks/semaphores etc. So instead of relying on an OS provided API like `pthreads`, you can use some of that magic yourself. What's interesting to me is how much things are similar to a distributed system. Indeed, a lot of the talks about consistency models etc. comes from that. And it's a good example of a synchronous system.

[Implementing Stripe-like idempotency keys in Postgres (2017)](https://brandur.org/idempotency-keys) - dealing with non-transactional systems is hard, because the developer is in charge of the "transaction". The author here gives a rather involved example, with multiple DB writes and calls to external systems. But this is something any medium webapp will deal with at some point, so it's crucial to have some good patterns and tools for working with these cases.

[Async IO on Linux: select, poll and epoll (2017)](https://jvns.ca/blog/2017/06/03/async-io-on-linux--select--poll--and-epoll/) - at the heart of modern webservers like Nginx and event-based runtimes like Node and Golang's one we can find an "event" system. Which is a way to structure the computation for efficient execution on a single thread. Many of said events are IO related, and the `select`, `poll` and `epoll` syscalls are the standard interfaces for being notified of IO events.

[Datastructures for external memory (2016)](http://blog.omega-prime.co.uk/2016/07/05/datastructures-for-external-memory/) - speaks a little bit about B-Trees and LSM trees and how they're used by the storage engines of relational and NoSQL databases. It's really interesting how various variants of B-Trees essentially are specialization of the so-called B-$$\epsilon$$ trees.

[User interface design for programmers (2001)](https://www.joelonsoftware.com/2001/10/24/user-interface-design-for-programmers/) - a series of Joel Spolsky blog articles meshed into a small ebook. Covers some core user interface design principled - things that should always be top of mind and perennial. It's a longer read, but well worth it for anyone whose software has users.

[Apache Spark @scale: a 60TB+ production use case (2016)](https://code.facebook.com/posts/1671373793181703/apache-spark-scale-a-60-tb-production-use-case/) - Facebook wanted to update some of their ML pipelines to Spark and this is a recollection of what that entailed. It seems to have been a massive effort. Both engineering wise inside the company, but as well as contributing back to Spark. If anything, the Spark project benefited a lot from the changes needed in order to get it to run at scale. And "we all" benefited from that as well.
