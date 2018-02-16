---
published: true
layout: post
date: '2018-02-16 08:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #28'
---

A focus on probabilistic data structures with some Bitcoin thrown in this week.

[Probabilistic data structures for web analytics and data mining (2012)](https://highlyscalable.wordpress.com/2012/05/01/probabilistic-structures-web-analytics-data-mining/) - an article I've wanted to read for a long time. It covers Bloom Filteres, HyperLogLog counters, Count-Min Sketches and all that nice stuff and it also has a bunch of examples and real-world numbers for applications. There's a bunch of formulas, but not proofs or intuitions behind why they happen. That's a tall taks in general, since there's a lot of non-intuitive material to cover.

[Sketching data structures (2010)](http://lkozma.net/blog/sketching-data-structures/) - just a small introduction to Bloom filters and count min sketches, with some analogies.

[Probabilistic data structure showdown: cuckoo filters vs Bloom filters (2016)](http://blog.fastforwardlabs.com/2016/11/23/probabilistic-data-structure-showdown-cuckoo.html) - a comparison of the two and an introduction to Cuckoo filters. The Bloom filters used are counting ones, which allow for deletion. It's a bigger data structure than a regular one, but it makes for a fair comparison to Cuckoo filters.

[On-call at any size (2017)](https://increment.com/on-call/on-call-at-any-size/) - presents on-call practices for companies of 10, 11-100, 101-1000, 1001-10000 and 10000+ engineers. It's really interesting how on-call and the nature of keeping systems up changes from small to huge. On one end of the spectrum there's a lot of manual shepharding, while at the other there's basically a statistical understanding of what the system should be doing. And failure, loads and loads of failure.

[Updating navifation for StackOverflow, Enterprise, and Stack Exchange Sites (2018)](https://stackoverflow.blog/2018/02/08/information-architecture-navigating-stack-overflow-enterprise-stack-exchange-sites/) - an overview of recent UI changes to SO and the process behind them. Some details about the upcoming [channels](https://stackoverflow.com/channels) feature.

[How the Bitcoin protocol actually works (2013)](http://www.michaelnielsen.org/ddi/how-the-bitcoin-protocol-actually-works/) - Even though I knew about Bitcoin since forever I didn't take the time to properly understand it. Which is a shame, because even cursory glances suggested that it's seriously cool tech. Apart from all the hype and mania surrounding it. The author is Michael Nielsen, who's something of a polymath, operating in quantum computing, deep learning, networks theory and apparently distributed systems. The article doesn't disappoint - it's a very lucid presentation of what one might want out of a digital currency and how to go about doing that - ending up with Bitcoin at the end.
