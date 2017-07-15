---
published: true
title: "Friday Blast #1"
layout: post
date: 2017-07-14 15:15
categories: post
tags: friday_blast links
comments: true
math: false
---

This is the first in what I want to be a weekly series of posts. It's nothing fancy, just a bunch of articles I found interesting over the last week.

[URLs are UI](https://www.hanselman.com/blog/URLsAreUI.aspx) - a short and to the point article about a very basic thing, namely how URLs behave as UI and should be treated with the same care. Every voice counts however in the battle against machine URLs.

[Serverless Architectures](https://martinfowler.com/articles/serverless.html) - an introduction and overview to serverless and its main trends. The _shortcomings_ part is very poignant, given that much marketing material would have you believe serverless is the next sliced bread. As usual with articles on Martin Fowler's website, this one is well researched and supported by a lot of their in-house experience.

[Developer experience lessons operating a serverless-like platform at Netflix](https://medium.com/netflix-techblog/developer-experience-lessons-operating-a-serverless-like-platform-at-netflix-a8bbd5b899a0) - a case-study in running a serverless platform at Netflix. The product is aimed at external developers, rather than internal ones, and is very targeted. Nevertheless, the same sort of issues crop up as in more general platforms, which I found insightful.

[Scaling your API with rate limiters](https://stripe.com/blog/rate-limiters) - from Stripe Engineering comes this nice introductory piece to the uses of rate-limiters. There's a good discussion on rate limiters vs load shedders and when to use which. Some details about how to use them in practice, but I'd have liked more details about the actual implementation - what backing store they use, what criteria they consider in rate-limiting etc.

[Designing robust and predictable APIs with idempotency](https://stripe.com/blog/idempotency) - another one from Stripe Engineering, and equally as good. I especially liked the mention of the _idempotency keys_, which is the first time I've seen written about a pattern I've oft encountered in practice.

[You probably shouldn't use DynamoDB](https://syslog.ravelin.com/you-probably-shouldnt-use-dynamodb-89143c1287ca) - an article written out of experience. The numbers quoted seem quite small though. Small enough to make DynamoDB seem useless or at least very constrained in it's uses. As always, you can push Postgres/MySQL + Redis to do massive things, so don't jump into NoSQL unless you have to.

[Where do type systems come from](http://blog.felipe.rs/2017/07/07/where-do-type-systems-come-from/) - a change of pace in this article about the mathematical logic origins of type systems. There's a lot of punch for such a small article so I definitely say it's worth the read. But if you don't, the _tl;dr_ is that type systems were invented by logicians at the start of the last century to deal with paradoxes arising from "untyped" approaches to formalizing all of mathematics. The attempts didn't and [couldn't work](https://en.wikipedia.org/wiki/G%C3%B6del%27s_incompleteness_theorems) but found out renewed applications in computer science and programming language theory some 50 years later. Because even if we can't prove everything about a program, we still are interested in proving _some_ things, and types provide the infrastructure for this. 


