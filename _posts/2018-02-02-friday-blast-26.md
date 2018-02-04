---
published: true
layout: post
date: '2018-02-02 16:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #26'
---

[Understanding the C++ memory model (2018)](https://davmac.wordpress.com/2018/01/28/understanding-the-c-c-memory-model/) - a brief discussion on atomic operations and memory barriers and what they mean in the context of C/C++ (and many other languages at the same level of abstraction - Java, C#, Rust etc). Atomics are used to guarantee that certain very basic operations happen as a unit. Things like incremeting, compare-and-swap, compare-and-test etc. The set of atomic operations for a particular object forms a total order. However, this implies nothing for other objects or for visibility of other operations. For that, memory barriers are needed. C/C++ have the notion of acquire and release barriers, which guarantee that all operations before, respectively after, won't be reordered past the barrier. Barriers say nothing about atomicity. So you need both as a basis for concurrency primitives.

[Software complexity is killing us (2018)](https://www.simplethread.com/software-complexity-killing-us/) - the main argument is really that businesses are really complex these days. There's a lot of software which needs to do things and then a lot of interconnections between those pieces of software. Think things like - AD needs to know about new people joining the company from the HR system. OSS has been really good at providing the building blocks for software, so we don't need to reimplement the OS/core libraries/UI frameworks/data storage etc. But higher than that there's not much to work with. And that's where a lot of the complexity in a business setting comes from.

[Terraforming 1Password (2018)](https://blog.agilebits.com/2018/01/25/terraforming-1password/) - the story of how 1Password switched their infrastructure config from [CloudFormation](https://aws.amazon.com/cloudformation/) to [Terraform](https://www.terraform.io/). Both are neat tools for Infrastructure as Code, but Terraform was the better tool for them. In my experience that was the case as well - writing YAML and the abstractions of Terraform are better than writing JSON and those of CF.

[An infrastructure guide for founders (2017)](https://medium.com/starting-up-security/an-infrastructure-guide-for-founders-bbada8431fb1) - this isn't as broad as the title makes it out, but it's still relevant. Basically, you should think from the start about how to handle application logs&monitoring, the structure of AWS/GCP accounts and the software engineering around infrastructure. Common sense advice really.
