---
published: true
layout: post
date: '2018-08-17 07:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #49'
---
[What do you believe now that you didn't five years ago (2018)](http://highscalability.com/blog/2018/8/13/what-do-you-believe-now-that-you-didnt-five-years-ago.html) - interesting read about centralized vs decentralized systems. And how five years ago people _believed_ they'd take over (I mean, more than in the case of email, the WWW etc), and that hasn't really happened. And it's probably _never going to_ the way proponents would want.

[For mathematicians, = does not mean equality (2018)](https://jeremykun.com/2018/04/13/for-mathematicians-does-not-mean-equality/) - it means what they want it to mean. Much more so than programming languages, mathematics depends a lot on the context of readers. While things could be done super-formally, nobody does it. This article explains why, and how the simplest of mathematical notations carry a lot of baggage.

[Operationalizing Node.js for Server Side Rendering (2018)](https://medium.com/airbnb-engineering/operationalizing-node-js-for-server-side-rendering-c5ba718acfc9) - well, if this won't put you off SSR. An interesting article from AirBnB on how they slowly migrated from a Rails "regular rendering setup", to a SSR frankenstein to a simpler SSR. In all cases, the fact that we're dealing with a compute-intensive operation changes the calculus of building such services. From how you allocate machines, to what happens when there's more requests than capacity for them. In _backend land_, we don't give enough credit to how puny the computation we do is relative to the I/O, and how easy that makes our life.

[Circular law for random matrices (2018)](https://www.johndcook.com/blog/2018/07/27/circular-law/) - applied math warning. The eigenvalues of random matrices (ie matrices with components drawn at random from some distribution), neatly fill the complex unit circle under mild assumptions.

[Scaling consistency (2018)](https://lethain.com//scaling-consistency/) - how to build "cross-sectional" _review boards_, _architecture committees_ etc in growing organisations so that they'll have the maximum impact and least repercussions. Stuff you can't read in books.

[Learning market dynamics for optimal pricing (2018)](https://medium.com/airbnb-engineering/learning-market-dynamics-for-optimal-pricing-97cffbcc53e3) - a neat read about modelling problems. This is about predicting the price rooms in AirBnB will be rented at. There's a lot to unpack here, but the model is equal parts business knowledge, applied machine learning and old fashioned time series forecasting. I really dig it when I see systems like this being advertised. Sure, Deep Learning is all the rage, but a lot of stuff happening is mostly "the simplest model that'll work". In many cases that's a classical linear mode, or some tree etc. And in this case the powerful tools from classical statistics provided the juice to get the thing in a good state. Be on the lookout for some Fourier series as well.
