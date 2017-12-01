---
published: true
layout: post
date: '2017-12-01 11:00'
categories: post
tags: littles_law queing_theory
comments: true
math: true
title: Little's Law
---
I was recently reading [Java Concurrency In Practice](https://books.google.ro/books/about/Java_Concurrency_in_Practice.html) and came about this little gem of a theorem called [Little’s Law](https://en.m.wikipedia.org/wiki/Little%27s_law). It's quite intuitive and you've probably used it a bunch of times already. Still, I wasn't aware of it despite how useful and simple it is to state.

Little’s law is a result in the mathematical disciple of [queuing theory](https://en.m.wikipedia.org/wiki/Queueing_theory). This is the study of queues (duh). The formalism is simple. There is a system which processes work units. These arrive at various times, are processed and then they disappear from the system. There is some randomness involved both in the way work items arrive and in the way they are then processed, so the arrival rates and processing times are best modeled as random variables.

Many things can be modeled as queues. Queues with humans first and foremost, like the ones in a shop or movie theater. But also the processing of requests by a server, or the messages in a message queue and other IT related topics.

Little's law ties together the average number of work units arriving per time unit (the average arrival rate$$\lambda$$), the average processing duration (average time $$T$$), and the average number of elements active in the queue $$N$$. These are simply $$N = \lambda T$$. Remarkably this holds regardless of the distributions for arrival times and durations. All that is asked is that the system be stable, that is, all work items are retired eventually, and non-preemptive, which means once a work item has been started it is never abandoned.

But why is it true? Well, the intuition is really nice. Let's take a discrete case where our time evolves in units of minutes. And then, on average, each minute $$20$$ customers arrive, and, again, on average they stay for $$10$$ minutes. So the first minute were going to have $$20$$ people, the next $$40$$ and so on, until the 10th minute where we'll have $$200$$ people in the system. After this new people will arrive, but some will also leave, cause they're done their stuff. So if $$20$$ arrive and $$20$$ leave on average, then we're at a steady state of $$200$$ people at any given minute, past the “initial setup". The final number is just the product of people arriving and time they stay.

For such a simple result, the math is tricky. Even the most intuitive proof published was way beyond my desire to put in the effort to understand it. But the tool is broad enough and intuitive enough that it doesn't require all that to be effective.
