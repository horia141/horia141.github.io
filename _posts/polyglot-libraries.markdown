---
layout: post
title: Polyglot Libraries (And Frameworks)
date: {}
categories: post
tags: >-
  programming_languages software_development software_engineering library
  framework
comments: false
published: true
---
The name _Polyglot Library_ is one I propose for those libraries which appear in more than one programming language. The most famous example of this is, perhaps, the xUnit family of testing frameworks. While all of them are written in different languages, there's an undoubted conceptual core which is static, as well as a "tree of influence" between versions.

Testing is fertile ground for such libraries, with mockito, selenium etc. being ported to many different programming languages and platforms.

Quite related are libraries implementing "external" specs. Many templating languages fall into this category, and indeed, [mustache](http://mustache.github.io/) boasts more than 40 distinct programming language implementations. Thanks to the rather small feature set and required API, the implementations look fairly similar. I'd also put things like Protocol Buffers, Thrift, Avro etc. or the various JSON parsing libraries in this bucket, as well.

At a broader level, we can say that the library becomes an entity separate from the programming language. Given that more and more programming languages seem to develop a similar [feature set](http://horia141.com/string-interpolation.html), it will become easier and easier to express one successful library in the language of your choice.

Ideally, there would be a master list of such libraries. Part of a programming language's design team job would be to port these libraries to the new plaform. While raising the bar for implementation, it would radically lower the bar for early adopters, as they'd find all their favorite libraries in one place.
