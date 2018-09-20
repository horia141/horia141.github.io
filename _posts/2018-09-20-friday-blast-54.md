---
published: true
layout: post
date: '2018-09-20 07:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #54'
---
[Timeouts and cancellations for humans (2018)](https://vorpus.org/blog/timeouts-and-cancellation-for-humans/) - a precursor to the Trio article from [last week](https://horia141.com/friday-blast-53.html), this one deals with a more structured way to handle timeouts and cancellations in general. Like in that one, the notion of scope is married with the _cancel token_ of C# fame to get something really interesting. This one and the previous article have actually made me yearn for trying some of that scope based concurrency. I've also long had my suspicions that some of the ways in which timeouts are handled are not so great, and end up with additive timeouts if not downright incorrect code.

[50 years in tech: the Exxon delusion (2018)](https://mondaynote.com/50-years-intech-part-4-the-exxon-delusion-d92ada84f6e) - war stories from somebody who has almost twice as much tech experience as I have lived. Interesting that even in the 70s there was the notion of _data being the new oil_. Things are so fast in the tech industry, even our cycles are quick.

[Reinforcement learning - bandit problems (2018)](https://oneraynyday.github.io/ml/2018/05/03/Reinforcement-Learning-Bandit/) - I don't think folks'll get that much from this without some prior "bandits context", but for me it was a refresher. A nice tidbit, I've wanted to write about for some time, which this article mentions. One can think of "A/B testing", "bandit problems" and "reinforcement learning" as very related techniques, in increasing order of complexity. For the first one, everything is static and predetermined wrt the actions that must be taken. For the bandit case, we're allowed to learn globally about which actions are good and which are not and adjust things accordingly. For the reinforcement learning case we can learn _locally_ (that is, consider the state in which the system is), and work from there.

[Computing SVDs and pseudoinverses (2018)](https://www.johndcook.com/blog/2018/05/05/svd/) - the SVD is a workhorse of linear algebra, and a nice theoretical thing to boot - how many "things" apply to all matrices, for example? The pseudoinverses has the same relationship to the inverse as the SVD has to the diagnoalization. It pops up a lot in practice as well - in the same setups. Approximations of best solutions etc.

[Why we built Docker? (2013)](https://www.youtube.com/watch?v=3N3n9FzebAA) - back when Docker was just 3 months old, it's creator gave this very cogent talk about what sort of issues Docker would solve and what they hoped it would do to the tech ecosystem. In the end it did a bunch more than that, but somehow it feels like _it's still not there yet_. Just 5 years ago.
