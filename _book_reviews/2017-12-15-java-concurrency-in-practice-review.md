---
published: true
layout: post
date: '2017-12-15 08:30'
categories: post
tags: book_review
comments: true
math: false
title: 'Java Concurrency In Practice Review'
---
This is a book review for [Java Concurrency In Practice](http://jcip.net/), by Brian Goetz, Tim Peierls, Joshua Bloch, Joseph Bowbeer, David Holmes and Doug Lea. The author's are a who's who of the Java world. The _tl;dr_ is that this is a very good book and you should go out and read it[1]. I didn't have that much experience with modern concurrent programming, past basic threads/processes and lock-based concurrency, and I feel much better informed and prepared after reading this book.

This is a relatively short book, at roughly 350 pages, and mostly an easy read. The target audience is Java programmers who want to dig a little deeper into concurrency. And the book delivers. It looks at both the concurrency tools from Java 5.0 and 6.0 - queues, locks, thread pools etc, and at the lower-level primitives for concurrency - atomics, wait/notify etc. Finally, there's just standard discussions of concurrency issues: race conditions, data races, safety and liveness issues etc.

There's four parts to the book, all roughly equal in length, but going from "beginner" to advanced.

The first part, "Fundamentals", deals with the standard problems of concurrency and how an application engineer should view them. Things like safety and liveness, atomicity, when issues occur, basic synchronization in Java etc. are handled here. There's a bunch of examples of _bad_ code and of _good_ code. Which is a thing they keep through the book and is a real highlight of the book. The bad code especially is good as a little puzzle of what can go wrong.

The second part, "Structuring Concurrent Applications" is a bit higher level and introduces a lot of the newer APIs in Java, like `Executor`s, an in-depth discussion of approaches to cancellation and interruption, thread pools and `ThreadPoolExecutor`. There's even a discussion on GUI applications. It's not so relevant anymore for desktop Java, but for Android it might be useful.

The third part, "Liveness, Performance, And Testing", deals first with the bane of concurrent programs: deadlocks and other concurrency liveness issues. While the first parts have focused on safety - getting code that doesn't misbehave and doesn't have data races etc, this part focused on code which actually manages to do something, and doesn't get stuck waiting for a lock it can't get etc. Performance and scalability of concurrent programs comes as a natural extension to this. Finally, some issues on testing concurrent programs close the section.

The last part, "Advanced Topics", deals with the new explicit locks in Java 5/6 - `Lock`, `ReentrantLock`, `ReadWriteLock`, issues of fairness in lock-selection (which was an interesting concept especially wrt the performance implications), building custom objects that "synchronize" like locks etc. There is a discussion on atomic variables and some nifty non-blocking algorithms, and, finally, a short presentation of the Java Memory Model. I liked how it was defined in terms of the ["happens-before" relationship](https://en.wikipedia.org/wiki/Happened-before) from distributed programming.

One thing I liked about this book is that it has a wider applicability than just Java. Many of the concepts and issues discussed are very general and apply to any concurrent program, and indeed, any distributed system. But even the discussion of specific Java APIs is reusable, since, for example, C# and to a lesser-extent C++/Rust/C have very similar semantics for their memory models, similar APIs etc.

Anywho, give the book a try and you won't regret it.

---
[1] This is mostly going to be the standard review. It's really not worth it to read books which aren't great for "general" topics, since they're so many of them. I wager that if I _had_ to get into algebraic topology on manifolds or some other esoteric field, I'd power through a bad book. But it's not the case here.
