---
published: true
layout: post
date: '2022-05-10 07:00'
categories: post
tags: book_review
comments: true
math: true
title: 'Building Mobile Apps At Scale Review'
---
This is my review of [Building Mobile Apps At Scale](https://www.mobileatscale.com/). I wanted to read this
book to better understand the challenges of building complex mobile apps. My teams have relatively recently
expanded to include mobile engineers, so I primarily wanted to have enough of a grounding in this tech space
so I could have a decent conversation. Turns out a lot of the complexities are the same as in backend or web
development. They're just accentuated by the distribution channel of app stores. But I believe a lot of the modern
and common sense approaches to development - automated testing, CI/CD, progressive releases, etc. - carry over.

The book is divided into five major sections. The first deals with the challanges of building mobile
applications. We have all the usual suspects here. Releases through app stores and much slower rollouts
than "the web" take the lion's share of focus here. Through their various incarnations. But there's
also a section on state management, one on deeplinks, and in-app purchases. Which to be fair I had not
considered as _problematic_ up until reading this.

The second deals with challenges related to application complexity. Turns out navigation, application state
management, localization, and testing are all tricky things to do. I do have a bunch of desktop development
experience, and indeed mobile apps are much more similar to this, than to web apps. But while there you
could hind behind a simpler MVC & menu navigation approach, you can't in the mobile space. Navigation itself
is a big problem. But also the sheer complexity of starting the app in "the middle".

The third section is about engineering management in a way. It covers how to organise teams at the people, process
and tech level to be able to deliver well well into the hundreds. Things like stream-aligned teams and mobile
platform teams rear their heads up here.

The fourth section veers into cross-platform discussions. We recently did research at work about this very topic.
And 10ish years into the "mobile revolution" the story is quite sad. There isn't a clear winner, nor does there
seem to be a _desire_ for something like this. React Native, Kotlin Multiplatform Native, and Flutter stood
out here, but they all targeted slighting different use-cases, making clear comparisons hard.

The final section was about "stepping up the game". This was the section most reminiscent of the complexities of
large scale web and backend development. The chapter spoke about experimentation, feature flags, analytics, oncall,
quality checks and the complexities of migrations. These are realistically things that only bite you at a certain scale.
So I guess the pain isn't _real_ until you feel it, and a book can't do it justice.

While overall the content of the book was great, one part that I didn't enjoy as much was the product
placement. There were a lot of segways from "problem" to "product sponsor". While in general the suggestions
were best-in-class and you wouldn't go wrong with selecting them, it did feel a bit like paying for a
subscription and getting ads too. Worst of both worlds.

Regardless, this is a good book to read. I found it useful as a person with a non-mobile background. But I'd
definitely see it helping folks in with a mobile background, just at a smaller scale.
