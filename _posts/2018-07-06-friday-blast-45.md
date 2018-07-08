---
published: true
layout: post
date: '2018-07-06 07:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #45'
---

[Digg's v4 launch: an optimism born of necessity (2018)](https://lethain.com//digg-v4/) - I love war stories like these. Digg was big in the day, before _something happened_ and it wasn't. The massive and borked v3.5->v4 migration was widely blamed for it's downfall, though the story isn't always as simple. An interesting view into why things broke. And Python's stupid default parameters behavior.

[Vue.js: the good, the meh, and the ugly (2018)](https://medium.com/@Pier/vue-js-the-good-the-meh-and-the-ugly-82800bbe6684) - Nice overview of where Vue.js is right now. I _do_ think that you're basically OK with any of the big choices nowadays - Angular, React or Vue. In [RetroFeed](https://horia141.com/retrofeed.html), I'll actually be experimenting with doing less SPA magic, and more good-old-fashioned rendering, cause I think there's a pretty good sweet spot to be had with React in this fashion.

[H3: Uber's hexagonal hierarchival spacial index (2018)](https://eng.uber.com/h3/) - an overview of Uber's H3 library, whose name is an homage to Google's [S2](http://s2geometry.io/). Both are _geo_ libraries which offer various forms of geo-hashing - mapping coordinates to strings with nice properties and back again. H3 seems to be the more advanced version now - it uses hexes and has all sorts of nice error properties, whereas S2 uses quads.

[Least squares solutions to over-or underdetermined systems (2018)](https://www.johndcook.com/blog/2018/05/06/least-squares/) - one of my biggest "aha" moments was when studying applied linear algebra and approximate solutions to linear equations and seeing that sometimes you don't need the _exact_ solution. And getting one which is _close_ to the one sometimes is good enough. And many times is the only thing you can get, as there's no real _solution_ to speak of. There's a lot of power in this idea of not wanting the _best_ solution, but still finding a good one - from approximate methods to NP problems to Baeysian optimization etc. This particular case is just for linear systems, but the same thing appears a lot in statistics, ML etc.
