---
published: true
layout: post
date: '2018-08-24 18:00'
categories: post
tags: book_review
comments: true
math: false
title: 'Spatial Data Analysis Review'
---
It's been almost _three months_ since I did one of [these things](https://horia141.com/the-next-100-years-review.html). Not great. So this is my review of [Spatial Data Analysis](https://global.oup.com/academic/product/spatial-data-analysis-9780199554324?cc=ro&lang=en&) by Christopher Lloyd.

I primarily bought this book _for work_, since we're doing a lot of geo and maps work at Taxify. We are hiring [by the way](https://taxify.eu/careers/). I was looking for a book which would provide an introduction to computational issues around “geography” - things like projections, geohashes, routing, computational geometry etc. I was also secretly hoping for a refresher on _basic_ geography itself, cause it's been 20 years since I did that stuff in school. And by just judging the book by it's ToC it looked like it would fit the bill.

The good part was that a lot of the stuff I wanted to _know about_ got a mention. The bad part was that it was usually very brief. Enough for me to Google and be awere of new stuff. But as I said I was hoping for a more self-contained thing. OTOH, the main focus was on statistics - both _general_ and spatial data specific method. And on this front it did pretty well. Again, it didn't go into a lot of details, but I did manage to get the gist of kerning / gaussian process regression from here. Which ML books have been unable to make me understand for example. The size of the thing wasn't that great to boot, so overall it wasn't a big investment. Which I think makes reading it a net positive.

I'll highlight some of the more interesting chapters.

Chapter 6 deals with network analysis. This is a big field in itself and is basically a combination of graph theory with a dose of statistics and a heavy slant towards real world applications. Naturally the road networks are the main subject here. And both routing algorithms are discussed (though only at the level of Dijkstra), as well as [_network theory_](https://en.wikipedia.org/wiki/Network_theory) measures of the properties of a graph: centrality, diameter, sparseness measures etc.

Chapter 8 deals with ways to look at patterns in spatial data. The gist is mostly using classical statistical tools (linear regression) but applied in _windows_ across the spatial dataset. Looking for autocorrelation of spatial data there's a bunch of special measures for this, not just clean extensions.

Chapter 9, which is about spatial regression, was by far the most demanding and the one I felt I got the most out of. It deals with “completing” spatial data from missing values. Nearest neighbours methods of various sorts, triangulation, splines and locally weighted solutions are presented. But the big discussion is on krieging and it occupies the second half of this chapter. Here they did spend a lot of time on providing examples, building intuition etc. They started with some assumptions on data (dependence of variance in a measure only on distances between points for example), building a Variogram and then constructing GP regression as a nearest-neighbor / weighted mean informed by the variogram. It all reduces to a / some linear systems of equations. They don't go into details of where it comes, and AFAIK it's the result of some sort of optimization problem (cause Lagrangian multipliers crop up), but that's about as far as they took it. Still, pretty neat.

There's 6 others chapters as well to explore, a bit more _introductory_ than these ones, but still fundamentally interesting. As I mentioned, overall this was a positive experience.
