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
Many times, when somebody familiar with a programming language $foo, moves to a new programming language, $bar, they miss the nice libraries from $foo. So they end up writing a version of those libraries in $foo. This process tends to happen especially for the good libraries. So in time, 

So we end up having, what is essentially the same library, written in different languages.

The canonical example for this is xUnit, the unit testing library.

On the one hand, there's a software artefact which is bounded to a certain programming environment, and that's a boundary with a very high wall around it. On the other hand, it's undeniable that the same concepts are at play, and there's a common core to all of them. So I'm 


Quick question - have you ever used an xUnit library? You probably have? Which one though? JUnit (link)? CUnit (link)? unittest? RubyUnit etc?

We've recently seen the rise of libraries which span multiple languages. Polyglot libraries and 

Angular is a good example of a polyglot framework. It has a javascript, typescript and dart variant. Polymer as well.
Mockito is another library which seems to be universal. WebDriver.
React, ReactNative. Guice-like dependency injection.

It's gonna be harder for new libaries to compete at some point. And what works in one language is not necessariy what will work in another. Or perhaps more insisdious, two languages might be superficially the same, hence you tend to write the two libraries in a similar fashion, but not being Pythonic etc.

But in the end, if the reason to choose a language is also it's ecosystem, if all languages have the same ecosystem, the choice becomes moot.

On the flipside, what's needed for a language to be considered usable? No longer a compiler and a decent standard library. Currelt, that would be: compiler&dev kit, package manager & globally available repository, IDE interaction, large standard library and presence of some well known libraries for web development (or whatever nieche you're in really).

On the other hand, it becomes easier to sell switching to a new language if there's already all the needed tooling for it.
