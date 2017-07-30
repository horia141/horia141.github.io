---
published: true
title: "Explicit Entity State"
layout: post
date: 2017-08-01 10:10
categories: post
tags: database sql architecture entities
comments: true
math: true
---

Many or even most of the entities we work with in typical applications have a notion of distinct states they can be in. These states correspond to the evolution of that entity though the application, and the entity is expected to move from one state to another as a result of certain events happening.

To make things more concrete, consider a user entity. Typically a person joins a service and is then asked to confirm an email. After that the product is fully accessible. Later, the user might quit the application and remove their account. We can say that the user has three distinct states: joined, confirmed and left. Similarly, an ecommerce order is first placed, then payment is received, then the order is shipped. At any time before shipping an order can be cancelled. The states are more complex now, with a proper finite state machine as a model.

When laid out explicitly like this things are pretty good. The schema is self-documenting, it's easy for application code to filter and make assumptions about which columns are valid for a given state, and our own understanding of the code is made easy by this systematization of the possible states of an entity.

However, many times this is not the case. That is, there is no single state column to record explicitly the state an entity is in, and changes to it don't happen as a result of a small set of well defined events. Rather, states are implicit in assignments of various fields. A common pattern I've seen is marking removal via an `IsRemoved` field or a `DateRemoval` field, which is not null once the entity is removed.

With two states, such an encoding does not cause problems, but is not nice either. However, when we begin adding other fields like `HasAcceptedEmail` or `HasShipped` etc. things begin to break down. It's not clear when any of the $$2^n$$ state combinations is allowed, it's harder to filter based on states and the code becomes more complex as a result.

So I'd call this a pretty nasty anti pattern. It's not easy to solve, as any database refactoring truthfully is. But as a first approach, it does serve to add the explicit state column, and try to maintain it accordingly, while also doing any individual field work in parallel. Once you’re convinced that the state handling is correct, one can remove fields like `IsRemoved` or `HasShipped`, and leave fields such as `DateRemoval` for faster access in a denormalized fashion.
