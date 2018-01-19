---
published: true
layout: post
date: '2018-01-19 16:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #24'
---

A video heavy link set today. Hope you enjoy.

[Advice for first time founders (2017)](https://blog.ycombinator.com/advice-for-first-time-founders/) - nuggets of wisdom from YC founders to first time founders. Hiring/firing and knowing the customer seem to be the most common things.

[How we made the microprocessor (2017)](https://www.nature.com/articles/s41928-017-0014-8) - a small bit of the history of the first microprocessor - not 8086, not 8008, but 4004.

[Efficient analytics with Redis bitmaps (2017) #talk](https://www.youtube.com/watch?v=a-BtWlU55kk&mkt_tok=eyJpIjoiTURrMk9UVmtZVGMzWWpBNSIsInQiOiJmWHdNN2c2WG5xc1ZcL3JGdjI3YzF5TFlEVm5jZ3ZnVVpXb2Y4RFo4bkVBSUZKQXp4Q2FlQlFTdDRvSmwyMGtnWWY3UDFYOEpkQW9CbWxxamYrWDBtUXhFZHdoc0RPUUdmdjNCKzhWUE1IZVpJcVJoNGRyeGREYTJNdm5EWjRPM1EifQ%3D%3D) - Another Redis based talk and an example of using Redis' bitmaps for analytics. Bitmaps are a datatype, much like lists or sets, so working with them feels quite natural in Redis. The usage described here is quite similar to how some databases optimize analytics queries via fast bitmap operations.

[Transactions: myths, surprises and opportunities (2015) #talk](https://www.youtube.com/watch?v=5ZjhNTM8XU8) - basically covers ACID, Isolation Levels and serialization anomalies plus a bit of history about how they came about. Entertaining speaker and nice presentation of the concepts.

[Purely functional datastructures (2015) #talk](https://www.youtube.com/watch?v=KtltiBfvqCE) - a brief introduction to a very interesting topic - building data-structures without mutation & persistent datastructures. The speaker managed to cover stacks and queues. Not to dissapoint, the topics are quite hard. Even the simple queue ends up being quite complex when designed to be immutable/persistent _and_ performant.
