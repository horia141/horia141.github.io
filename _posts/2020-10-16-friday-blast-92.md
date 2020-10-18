---
published: true
layout: post
date: '2020-10-16 07:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #92'
---
[Why do ARM chips have instructions with JavaScript in the name (2018)](https://stackoverflow.com/questions/50966676/why-do-arm-chips-have-an-instruction-with-javascript-in-the-name-fjcvtzs) - 
remember kids, if your programming language becomes popular enough, its primitive operations will become CPU
instructions. I wonder if there's been any analysis done on this? Like look at where a sufficient sample of programs
spend their time and make that into instructions. You'd need a size/complexity heuristic to not just leave it at
`main` but I'm sure companies such as Google or AWS which run big sever workloads would have the data.

[Why isn't functional programming the norm? (2019) #video](https://www.youtube.com/watch?v=QyJZzq0v7Z4&feature=youtu.be) - 
the short answer is "it's complicated". The longer answer is that FP languages lack either a "killer app" or some
serious corporate backing. Add do that a bit of a definitional problem - like what is an FP language? Is Common Lips
where you can have imperative constructs more FP than Rust where everything is immutable by default? OTOH many modern
languages have functional programming capabilities, so in that sense FP is the _present_.

[The observer effect with Daniel Ek (2020)](https://www.theobservereffect.org/daniel.html) - an interview with
Spotify's CEO. There's a lot to take in, but perhaps for me the most interesting part was about the coaching he provides
to his reports.

[AirBnBaller (2020)](https://www.profgalloway.com/airbnballer/) - an analysis of why in the long run AirBnB might be the
"breakout" startup of the 2010s, eclipsing the likes of Uber, or Palantir. Right now, things are dire with the global
pandemic, but it won't last forever. If anything, as a supply gateway AirBnB will have a very strong hand to play vs
traditional hotel chains.

[40ms of latency that just won't go away (2020)](http://rachelbythebay.com/w/2020/10/14/lag/) - another case of being
tripped up by Neagle's algorithm for TCP - which batches short message bursts into bigger chunks to more efficiently
utilize bandwidth. At the expense of latency. Disabling it is set via some flag on the socket. What I always find
peculiar about these low level APIs is how much they had that you're doing a "big thing(tm)" with these things.Sometimes 
it's not even clear it works or is enough to work. I definitely like the higher level API where
you'd instantiate a `NoBufferingConnection` or something of the sort and make it really clear and
semantic what you're trying to achive.

