---
published: true
layout: post
date: '2020-10-23 07:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #93'
---
[Taming floating point error (2020)](https://www.johnbcoughlin.com/posts/floating-point-axiom/) - a brief overview of what
error means in _floating point_ and how it affects work. What I found most interesting was the discussion on
error analysis and error propagation through a computation. This was one area I didn't have a good mental model of
how to approach from uni days, and it turns out that (at least conceptually) it is quite straightforward and elegant.
Indeed, I have an even higher appreciaton for the design of the floating point standard now.

[Bloom filters debunked (2020)](https://gopiandcode.uk/logs/log-bloomfilters-debunked.html) - apparently there was an
error in the analysis of Bloom filters false positive rates lurking for 30 years. Indeed the last step of the analysis
seemed a bit hand-wavy the first time I encountered it. The authors used `coq` to provide a formal proof of the
known correct form and increase our confidence in it.

[On the uses of a life (2020)](http://www.daemonology.net/blog/2020-09-20-On-the-use-of-a-life.html) - the author of
`tarsnap` (and inventor of key derivation methods in cryptography) got called out that essentially he wasted his life
making backup software. This is his response.

[Finding the right company to reach Staff engineer (2020)](https://lethain.com/finding-the-right-company/) - another
one from Will Larson. Staff roles are those very-senior engineering roles in a company, and the article is about
alignment and expectation setting in order to reach that.

[What engineering managers should do and why we don't (2019) #video](https://www.youtube.com/watch?v=Q_bJVokYLRI&feature=youtu.be) -
a short introduction to management for engineers. In video form.
