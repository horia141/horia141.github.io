---
published: true
layout: post
date: '2019-10-25 07:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #80'
---
[Announcing TypeScript 3.7 RC (2019)](https://devblogs.microsoft.com/typescript/announcing-typescript-3-7-rc/) - the latest TS contains a bunch of neat features like the `?.` accessor and the `??` operator for simpler interaction with `undefined`. I know a lot of the code I write would benefit from this. Sad that Dart has had this bit of syntactic sugar since a billion years ago tho.

[Simon Marlow, Simon Peyton Jones, and Satnam Singh win most influential ICFP paper award (2019)](https://engineering.fb.com/security/simon-marlow/) - the paper in question is from 2009 and focuses on multicore support for Haskell. What's interesting though is that there's a project called [Sigma](https://engineering.fb.com/security/fighting-spam-with-haskell/) at Facebook, meant for abuse protection (anti-spam, phishing attacks, etc.), which serves more than 1M QPS. Which you can do in any language under the Sun for this sort of massively scalable problem, but only in a couple you can do it efficiently - apparently Haskell is one of them.

[In defence of design documents (2018)](https://riccomini.name/in-defense-of-design-documents) - writing up some guidelines for design docs at work, and read this small article for research. Read on if you haven't been exposed to "design docs" as practiced by big tech companies.

[How Netflix microservices tackle dataset pub-sub (2019)](https://medium.com/netflix-techblog/how-netflix-microservices-tackle-dataset-pub-sub-4a068adcc9a) - an overview of Gutenberg, Netflix's system for _dataset pub/sub_. In other words, a system for managing "datasets" (ML models, config, other big data), and publishing these things to consumers.

[Designing file formats (2005)](https://www.fadden.com/tech/file-formats.html) - sage advice for designing a binary file format for your application. Things like identification bytes, header checksums, version numbers, data offsets, etc. are covered. Bonus points for reminding people to not load chunks of data and alias them as C structs!
