---
published: false
---
In this post I'll be looking at the effect on query performance of the distribution of values of the index used in the query.

A [devforum.ro post](https://devforum.ro/t/care-este-cel-mai-rapid-mod-de-interogare/4602/21) got me thinking about the subject. The OP asks why their query is running slow. Many hypotheses were put forth, but without extra info or feedback they couldn't be validated. A common theme was that OP should use an index. However, user @pghoratiu offered some sage advice: the distribution of the data of the column used as an index counts just as much when querying.

Intuitively this is true - a limit example would be a column with a single value, where the index would be useless for many types of queries.

But for "real-life" data, how much would it count? I was curious, so I set up a small experiment. I looked at three different distributions:

[ more details about how these distributions look like ]

- Uniform in a given interval: this is the distribution one would obtain for `id` columns or `guid`s, as well as for natural-ish fields such as names, emails etc. [ image ]
- Skewed towards smaller values: a canonical example would be 
- Very skewed
