---
published: true
layout: post
date: '2018-10-19 07:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #55'
---
[Thank you for your help, NoSQL, but we've got it from here (2018)](http://blog.memsql.com/nosql/) - More and more companies are realising that SQL can handle very large scales very well and that losing ACID, Schemas, SQL etc. isn't a price worth paying in most situations for the slight benefits a NoSQL solution offers. A nice quote "It’s not clear why schema was lost as part of the NoSQL movement." - I've often wondered why myself.

[Why we moved from MongoDB to PostgreSQL (2018)](https://dzone.com/articles/why-we-moved-from-nosql-mongodb-to-postgresql) - same vein as the previous one, though some of the reasoning about migrations is going to affect them.

[Goodbye microservices: from 100s of problem children to 1 superstar (2018)](https://segment.com/blog/goodbye-microservices/) - How Segment moved their data distribution service from one microservice per destination to a single monolith for all. Though the engineering reasoning is solid, and it _does seem_ the split into microservices was ill-thought to begin with. I'd read this as a cautionary tale for thinking really hard if the things you're splitting into services are really that independent. Technically, every function call could go to another service, but that'd be insane.

[YAML: probably not so great after all (2016)](https://arp242.net/weblog/yaml_probably_not_so_great_after_all.html) - apparently YAML is very big - bigger than XML even. I _had_ no idea. Ditto for the other complexities of representing objects. It's strange that after 70+ years of computing, there's still no universal way of representing configuration which is easy for humans to read, easy and unambiguous for computers to parse and emit and is well integrated with the programming languages of the day.

[Simplifying media innovation at Neflix with Archer (2018)](https://medium.com/netflix-techblog/simplifying-media-innovation-at-netflix-with-archer-3f8cbb0e2bcb) - in which Netflix details their Archer system. This is a tailor made big data platform for analyzing and processing videos. It's meant to make things easy and all sorts of media processing is built in. You get a MapReduce-like interface where video frames and even scenes are already split for you. There's a bunch more details, but I think it's a wonderful example of how building a tool like this can enable many other teams to do things they couldn't have before, because of the complexities involved.
