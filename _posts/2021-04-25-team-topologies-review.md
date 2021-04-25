---
published: true
layout: post
date: '2021-04-25 07:00'
categories: post
tags: book_review
comments: true
math: true
title: 'Team Topologies Review'
---
This is my review of [Team Topologies](https://teamtopologies.com/). It’s a management book (oh no, not again), which looks at some good patterns for organizing teams in larger organisations. It proposes a set of team types and team interaction modes between them which aim to maximize ownership, delivery, efficiency, etc.

The first part of the book looks essentially at the constraints we have when building engineering organisations. The major point is that the software we write and maintain is actually a sociotechnical system - it comprises the “code”/system itself, as well as the people building it. The people influence what gets built as much as the programming languages they’re using. And the people have a host of limitations: people suffer from a limited cognitive capacity to model a particular problem, people can remember and work with a limited number of other people ([Dunbar’s number](https://en.wikipedia.org/wiki/Dunbar%27s_number)), organization structure influences work output quite literally ([Conway’s law](https://en.wikipedia.org/wiki/Conway%27s_law)), etc.

This all means we need to look at the structure of the organisation building software just as much as we look at its architecture. 

The book has the premise that we consider the team to be the unit of "delivery", and not the individual, and that we want to optimize for delivery while keeping good ownership, long lived teams, career opportunities, etc. This is all reasonable stuff, and I've seen it expanded upon and better articulated in [Peopleware](https://horia141.com/peopleware-review.html).

There are then suggestions for four different types of "Topologies" for teams. We should aim for these, and not hybrids, or alternatives. These are: the stream aligned team, the platform team, the complicated subsystem team, and the enabling team. The stream aligned team is the classical fast delivery team with full ownership of what they do and how they do it. The majority of teams should be like this. The platform team is the classical infrastructure team which offers some services to other teams. The idea is to try to provide as much autonomy and control to client teams as possible, and not keep the team in the loop for every random request like adding a new machine or enabling a new API. Complex subsystem teams are meant to work on well separated, but complex pieces of systems. Think your video codecs, compression algorithms, routing engines, etc. Finally enabling teams work as leverages for other teams - they can many times work at the tooling and process layer, or by teaching other teams new methods, etc.

There are also three patterns for interaction: collaboration, offering a service, and facilitation. The main thing I got here is that offering a service should be the default interaction mode. Facilitation is something specific to enabling teams, or perhaps tiger teams yanked from the company for specific projects, but not something you'd expect every team to do. Curiously collaboration is seen in a bad light too. It is something which can payoff greatly, and is how projects should get started. But it is quite taxing on the teams, and requires a lot of dedication. So it should be used sparingly and there's even a suggestion that a team should not be collaborating with more than one team at a time.

There are two things I didn’t like about the book. First, the quantity of examples and their variety was not great. Much of the discussion looked at things in the abstract and relied on some common sense goals of team formation. The examples were usually case-studies of transformations from the “old model” to the “new one”, and I felt they just skimmed the surface of the complexities involved there. Second, there very few counter-examples.They provided the good team structures and interactions, but not really any of the suboptimal or bad ones. The Dev and Ops separation comes to mind, but that’ws about it. So one is left to wonder if the book is more descriptive than prescriptive.

In any case I definitely recommend this book. It’s changed the way I think about teams, and provided a set of good tools in my manager’s arsenal.
