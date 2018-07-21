---
published: true
layout: post
date: '2018-07-20 07:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #47'
---
[What I talk about when I talk about logging (2018)](https://hackernoon.com/what-i-talk-about-when-i-talk-about-logging-36237fad7336) - there's a lot to productionizing an Internet application which has to do with "logging". This article is a tour of all the boxes which need to be ticked for a _good_ setup.

[Eight-bit floating point (2018)](https://www.johndcook.com/blog/2018/04/15/eight-bit-floating-point/) - floating point isn't limited to the common `float` and `double` types of most programming languages. Rather it's a system of encoding numbers with variable precision. In this case just 8 bits. The graph with the distribution of numbers between IEEE and posit encoding is particularly enlightening. The same effect of having a higher density in more "common" intervals happens for regular encodings, just at much larger scales.

[Black-box auditing - verifying end-to-end replication integrity between MySQL and Redshift (2018)](https://engineeringblog.yelp.com/2018/04/black-box-auditing.html) - this one hits close to home. Checking system correctness above and beyond what testing offers is one of my hobbies. See [NValidate](https://github.com/horia141/nvalidate) for some work I published from my time at StackOverflow. Yelp's case study is similar - they're looking to make sure that they have the same data in MySQL as in Redshift. At it's core the system does a number of queries and hash comparisons to find out possible cases of inconsistencies. Well worth a read.

[Google Cloud Platform - the good, bad and ugly (it's mostly good) (2018)](https://www.deps.co/blog/google-cloud-platform-good-bad-ugly/) - an overview from a medium-sized user of GCP of what works and what doesn't. Echoes my experience as well, though I have more good things to say about their hosted Kubernetes offering and not so much experience with monitoring. The general idea is that GCP has less services, but they can be used in more ways than one (the comparison between Pub/Sub and SQS, SNS, MQ, Kinesis Data Streams, Kinesis Data Firehose, DynamoDB Streams is particularly apt), and they're generally higher quality.

[How Silicon Valley fuels an informal caste system (2018)](https://www.wired.com/story/how-silicon-valley-fuels-an-informal-caste-system/) - interesting read about the stratification of society in SV, particularly in San Francisco. Do take a read as my summary can't do it justice. But suffice to say that it's another datapoint in the "increasing economic inequality" phenomenon of the last 20 years. I wonder if the stratification is more visible because of the mono-industry setup of San Francisco. Because I think more or less the same thing happens in more diversified cities like New York, or London. But it might be masked by all the heterogeneity.

[Fibonacci Hashing - the optimization that the world forgot (2018)](https://probablydance.com/2018/06/16/fibonacci-hashing-the-optimization-that-the-world-forgot-or-a-better-alternative-to-integer-modulo/) - a way to perform the `% N` step of hashing for hash table usage with very nice properties. It is rooted in Fibonacci numbers. There's a very interesting analysis of the kind of reasoning needed when thinking about hash function behaviours, and some edge cases for anybody to be aware of wrt hash tables with numeric keys, for which "hashing" might just be `key % N` - a very bad setup.
