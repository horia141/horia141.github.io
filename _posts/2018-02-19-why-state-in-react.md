---
layout: post
title: "Why Does The State Object Exist In React?"
date: 2018-02-18 16:00:05
categories: post
tags: react design
comments: true
---

Use `@depiction` asks on StackOverflow [Why does state object exist in React?](https://stackoverflow.com/questions/48869892/why-does-state-object-exist-in-react/48870135#48870031). I've provided a biggish answer to the question, so I figured I'd add it to the blog as well. My answer follows:

First of, state is usually used to hold something local to the component which can be changed by user action or a push updates from the server etc. - something like whether a checkbox is ticked or not, or the input value from a textbox. The keyword is that it's local to the component and there's no reason for it to be "at the root of the class" (whatever that means precisely). There are extra constructs on top of that, such as redux/flux etc, and those are a bit more global, but it's not required for regular and small-scale React.

The same can be said about the usage of `setState` - it's a design decision. It's not needed, and React could probably use the same approach Angular does, which is scanning of component state fields changes on certain application-level events. It'd be even easier since all that's considered "state" is put into the `state` field, and all that influences rendering is in either `state` or `props` (and possibly `context`). But I find the very explicit `setState` approach much more reasonable - the points at which state changes and a render is triggered are much more well defined than Angular's "sometime in the future"/magic approach.

A related thing is that in React there's just a unidirectional data flow. Basically `DOM = f(State, Props)`. And any change to the state must be explicit. So for an `<input>` element, you'd supply a `value` attribute, but also an `onChange` attribute. The latter is a function invoked on a change, and it will, at some point `setState` and change the state field feeding into the `value` attribute (as part of the render). Contrast this to Angular where, AFAIK, you'd just supply the value and there would be a bi-directional data flow between the input and the state. It looks nicer locally, but it's a pain to work with when composing components - so much so that the pattern I've used most often in Angular for dealing with it was basically what React is doing. Again, a design constraint which makes you write more code, but also provides a much more saner development experience.

Overall React has a much stricter approach to building the UI than Angular does, or even jQuery or plain-ol-javascript. For some that's a bonus, for other's it's annoying. I've used all three, and I'd choose React for all future work.
