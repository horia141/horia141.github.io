---
published: true
layout: post
date: '2019-03-22 07:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #65'
---
[Open sourcing TonY - native support of TensorFlow on Hadoop (2018)](https://engineering.linkedin.com/blog/2018/09/open-sourcing-tony--native-support-of-tensorflow-on-hadoop) - an example of building an application on YARN (Hadoop's scheduler), which is similar to what Hadoop, Hive, Spark etc. do, but with a focus on TensorFlow. Size is quite small in the examples, but it's still a neat example.

[Algorithms behind modern storage systems (2018)](https://queue.acm.org/detail.cfm?id=3220266) - an ACM Queue article about B-trees and LSM-trees, which are the two major storage implementations for OLTP-type databases. Doesn't go into a lot of details, but enough to get an intro on them.

[Book review - how to write a lot - a practical guide to productive academic writing (2018)](http://muratbuffalo.blogspot.com/2018/04/book-review-how-to-write-lot-practical.html) - a review of a book review. So meta! It's a nice distillation and a lot of the suggestions apply to blog writing or any sort of technical writing a developer might find themselves doing - documentation, design docs, launch announcements etc. Very much similar to the advice from the [deep work review](https://horia141.com/deep-work-review.html) - write a lot in a dedicated time for writing basically.

[It doesn't have to be Turing complete to be useful (2018)](https://increment.com/programming-languages/turing-incomplete-advantages/) - a case for small Turing-incomplete languages as DSLs for narrow tasks. OTOH, it is _nice_ to have a Turing complete language in such cases - Gradle is an example which comes to mind from recent work.

[Google Maps' moat (2017)](https://www.justinobeirne.com/google-maps-moat/) - a "moat" is any feature/process/audience/etc a product has which protects it from its competitors. This is an analysis of Google Maps' _moat_. It comes down to _massive amounts of data_ and _a lot of engineers thrown at the problem_. What's interesting is that the _baseline_, from personal experience, to getting a usable experience with open source tools and data is not that hard to achieve. But getting to the level of Maps is nigh impossible.
