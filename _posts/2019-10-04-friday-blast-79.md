---
published: true
layout: post
date: '2019-10-04 07:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #79'
---
[Why printk() is so complicated (2019)](https://lwn.net/SubscriberLink/800946/a9ad9aba46f14e78/) - a deeper dive into the `printk` function from the Linux Kernel. Not really familiar with the kernel, except that it exists. But I had no idea something so "basic" as logging can turn into something to big. OTOH, in webapp land, it's not exactly trivial either to have good high-performance logging.

[Fixed points (2019)](https://www.johndcook.com/blog/2019/10/04/fixed-points/) - a bit about function fixed points. I remember encountering one of the theorems in the article a long time ago in a calculus book.

[HTTP/3 - the past, the present, and the future (2019)](https://blog.cloudflare.com/http3-the-past-present-and-future/) - turns out there's a 3rd version of the HTTP standard out. It's actually a simplification of HTTP/2, because it build on stream support in QUIC, so the same mechanism doesn't have to be reimplemented like with HTTP/2. It's mostly meant to address "head of line" blocking in case of transport errors by the looks of it. As extra commentary, does it seem to anyone that we're seeing a lot faster releases of fundamental tech in the last years. From programming languages (JS, Python, C#, Java, etc.), to protocols (HTTP with /2 and /3, TCP with QUIC, various secure DNS variants), to databases (Postgres 12 is out recently)?

[WeWork and counterfit capitalism (2019)](https://mattstoller.substack.com/p/wework-and-counterfeit-capitalism) - I've been following the WeWork story these couple of months, since it began to seem _not-so-ordinary_. Turns out it's a trainwreck of a situation. Their CEO is out because of `$shady` stuff, and the IPO is being withdrawn with a massive hit to the possible valuation. Loads of lessons to learn I'd imagine, but it really does point to how _free_ money is in these situations.

[Software architecture is overrated, clear and simple design is underrated (2019)](https://blog.pragmaticengineer.com/software-architecture-is-overrated/) - a rant against "architects" in the sense of folks making technical decisions without actual real-life involvement with the technology (like in coding, maintenance, operationalization, etc.). The places I've worked at and in the circumstances I could influence all had a holistic view of development, in the sense that a developer was responsible for the whole lifecycle of a feature. From design, speaking with stakeholders, coding, writing tests, and ending with releasing in "live" and handling operational behaviour. The difference between more senior and more junior engineers being in the scope of the work involved, rather than in it's _completeness_. I think this is a good and empowering approach for many/most situations.
