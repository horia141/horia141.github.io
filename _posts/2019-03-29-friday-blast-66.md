---
published: true
layout: post
date: '2019-03-29 07:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #66'
---
[On infrastructure at scale - a cascading failure of distributed systems (2019)](https://medium.com/@daniel.p.woods/on-infrastructure-at-scale-a-cascading-failure-of-distributed-systems-7cff2a3cd2df) - all the things that started failing in Target's infrastructure. It's a nice story of how complex systems interact. It even has oscillating behaviour.

[Laws of tech - commoditize your complement (2018)](https://www.gwern.net/Complement) - an article on Gwern.net about Joel Spolsky's _pattern_ of "comoditizing your complement". Or making sure a complementary product to yours has many providers, or is open source, or otherwise making it _easy and cheap_ for your customers to use. The bulk of the article is a long list of such occurences.

[Communication is a core skill for programmers (2019)](https://medium.com/@mquiros/communication-is-a-core-skill-for-programmers-ff61162bbe6d) - true words. So much of what an engineer does, especially as they become more senior, is _persuasion_ and effective communication. Design docs, postmortems, documentation, product pitches etc. are some day-to-day cases where this is needed. So it's best one is always practicing this skill.

[How fast can you multiply really big numbers? (2019)](https://www.johndcook.com/blog/2019/01/14/multiply-big-numbers/) - betcha you didn't know you can multiply numbers via the fast Fourier transform? And that it's faster for "big numbers" too - not just a theoretical exercise.

[How fast can you multiply matrics? (2018)](https://www.johndcook.com/blog/2018/08/31/how-fast-can-you-multiply-matrices/) - a complement to the other one. Strassen showed that you can do it in under $$O(n^3)$$ which sparked off a search to find the theoretical lower bound for this. It sits at $$O(n^2.37)$$ right now, with a natural limit of $$O(n^2)$$ which some folks believe is actually doable.
