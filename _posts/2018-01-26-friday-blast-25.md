---
published: true
layout: post
date: '2018-01-26 16:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #25'
---

[Ten year's worth of learning about pricing (2017)](http://tomtunguz.com/pricing-summary/) - this is not a tech link. But it's interesting none-the-less I think, for those many engineers which live next to the business side of whatever company they work for.

[Matrices from a geometric perspective (2008)](http://www.coranac.com/documents/geomatrix/) - switching it up to geometry. Understanding linear algebra is much easier when you have the geometric intuition. 

[Quick tips for fast code on the JVM (2018)](https://gist.github.com/djspiewak/464c11307cabc80171c90397d4ec34ef) - standard stuff. Define a hot path, and avoid allocations, boxing and megamorphic functions on it. Loads of examples of how things went wrong.

[The art of service discovery (2015) #talk](https://www.youtube.com/watch?v=27ynM2tbNXM) - Once a system grows past a couple of instances, service discovery becomes a thing. There's a bunch of solutions, depending on how big your problem is (hand-coded, DNS, Consul/etc, hand-crafted). This talk covers Netflix's custom built solution, with an overview of the architecture and some real-life challenges (mostly around what happens when service discovery is itself unavailable).

[Performance engineering at MasterCard (2015) #talk](https://www.youtube.com/watch?v=Fq97BvwoJbU) - general tips about "performance engineering". Many larger engineering organizations have specialized cross-functional roles like "testing engineer" or "security engineer". This talk is best summarized as what a "performance engineer does".

[Scalable stream processing: a survey of Storm, Samza, Spark and Flink (2016)](https://medium.baqend.com/real-time-stream-processors-a-survey-and-decision-guidance-6d248f692056) - another large piece from the folks at Baqend, this time focusing on various stream processing systems. These are duals/complements/replacements for batch processing systems like Hadoop/MapReduce.
