---
published: true
layout: post
date: '2018-06-22 07:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #43'
---

[Optimal low-rank matrix approximation (2018)](https://www.johndcook.com/blog/2018/05/07/truncated-svd/) - decomposing matrices into pieces is one of the workhorses of engineering and statistics (and applied math). Recommender systems, image compression, PCA etc. all can be reduced to some form of matrix decomposition. Here John Cook speaks about the optimal approximation, which is, for general matrices, the SVD (no surprise there). I really liked the expression of $$A = \sum_{i} \alpha_i u_i v_i^T$$. Makes it really clear just how "small" the decomposition can be.

[What every engineer should know about open source software licenses (2018)](https://eng.uber.com/oss-ip/) - there's a lot to know actually. From which licenses there are and the various families (copy left, Apache, MIT etc), to how and when to allow them in dependencies in code, to how to use them when open-sourcing company-time work. Good read overall.

[Subscription hell (2018) #hn-link](https://news.ycombinator.com/item?id=17007036) - a nice TechCrunch article about _where we're headed_ with subscription services. I'll have a short piece on this soon as well.

[Encoding vs encryption vs hashing vs obfuscation (2011)](https://danielmiessler.com/study/encoding-encryption-hashing-obfuscation/) - simply what each is. A working programmer encounters all of them, so it's good to be precise about these things.

[Migrations - the sole scalable fix to tech debt (2018)](https://lethain.com//migrations/) - here's an interesting piece. All organizationas, whether technical or not, accumulate tech debt. You have to clean it up sometime, lest it overwhelms you (and causes the breakdown of business processes as well). But the author, an experienced manager, argues that the solution is a _migration_, rather than constantly patching and fixing the status quo. A migration means a large scale move from one system / platform etc. to another, which implicitly adresess a lot of the issues currently faced by the organization.

[Chatbots were the next big thing - what happened? (2018)](https://blog.growthbot.org/chatbots-were-the-next-big-thing-what-happened) - the NLP just wasn't there yet. But it's more complicated than that - there were inflated expectations, UX issues to cross (text != GUIs we're used to), tech issues (many platforms were not ready to become chat-based). But as things evolve, and as AI problems become AI reality, we'll probably see chatbots make a comeback.
