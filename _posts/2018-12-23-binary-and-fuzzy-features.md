---
published: true
title: Binary And Fuzzy Features
layout: post
date: 2018-12-23T11:16:05.000Z
categories: post
tags: product_management software_engineering
comments: true
---
Today's topic is a bit different. We're gonna talk about product management and a way to interact with it as an engineer. Especially one working on consumer facing _Internet applications_. Thing Google, Facebook or [Taxify](https://careers.taxify.eu/).

The main thing you do as a developer is build _new stuff_. There's for sure mending work to do - bugfixing, refactoring, keeping an eye on things, and other aspects such as meetings, interviews etc, but your main time allotment should go to building new stuff. If it isn't, then ping me a message, cause we're hiring.

This new stuff can be either feature work or pilot / prototype work. Both can vary in scope and importance though and they aren't meant to be ordered. The small data analysis script might be brand new, but it's complexity might pale in comparison to adding support for multiple Foos in the Bar service.

Another classification is more interesting and where I wanted to get. Feature work can either have a binary success outcome or an analog / fuzzy one.

Let me elaborate. Things like adding a new API to an existing service, or a new screen for viewing user stats etc. are binary outcome ones - you either finish them or you don't in a given time allotment, and they usually drag along until they're finished. After which you you're done with them save for maintenance work. Launches are usually done via a feature flag and if there's a gradual rollout it's from user cohort to user cohort.

More involved are fuzzy outcome features. Code complete is just another milestone here. You're also interested in the behavior of the feature in the wild, and its effect on the business metrics you care about. Things like changing some ad bidding rules in an AdTech system, or how cars are allocated in a ride hailing app would be good examples. In general big and data driven systems, with a lot of moving parts and a lot of systems interacting to produce novel and emergent behaviours. Launches are usually done via one or more experiments, to check that the relevant metrics move in the right direction. Issues here can mean delays, reworks, complex debugging and even abandoning the work completely. There's always a strong element of data analysis - both at the experiment level, but also in debugging, figuring out user cohorts impacted negatively by the change etc.

Obviously the latter form sounds much harder than the former, and if you want an easy life you'll focus more on the binary than the fuzzy features. However, the latter are the ones which'll push you engineering wise, and which will have nice metrics to attach in the end. Furthermore, as companies and products grow and grow, most any feature becomes a fuzzy feature. Adding something simple as a new view to a product used by tens of millions of people is usually judged by a lot of quality metrics, making it in effect a fuzzy feature. Exposed to the same risks as well.

Of course real life is messy. A given feature is gonna lie somewhere between the two extremes. Binary features will have some sort of success criteria attached distinct from “it exists”. Similarly, parts of fuzzy outcome features can be integrated and used regardless of the main features outcome.

So what's the takeaway? Basically that as an engineer you need to be aware of this nature of the feature and plan accordingly for it. And in so much as you are able to push for it, invest in early data gathering and analysis work for fuzzy features, make the case for clear acceptance criteria, and try to structure the work in such a way such that elements of it, such as a good refactoring, can still make it into the final product, regardless of the overall success of the feature itself.
