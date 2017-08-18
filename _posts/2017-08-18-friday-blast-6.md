---
published: true
title: "Friday Blast #7"
layout: post
date: 2017-08-18 10:39
categories: post
tags: friday_blast links
comments: true
math: true
---

This week - Norbert Baum's claim of proof for $$P \neq NP$$.

[Norbert Baum on P versus NP (2017)](https://johncarlosbaez.wordpress.com/2017/08/15/norbert-blum-on-p-versus-np/) and [On Norbert Baum's claimed proof that P does not equal NP (2017)](https://lucatrevisan.wordpress.com/2017/08/15/on-norbert-blums-claimed-proof-that-p-does-not-equal-np/) - No cookies if you've guessed people are skeptical about the proof and holes have already begun to appear. The discussion is way above my pay grade, but I did manage to learn a little bit about [circuits and circuit complexity](https://en.wikipedia.org/wiki/Circuit_complexity) in TCS and, more interestingly, non-monotone circuits. These are circuits which don't have a NOT gate, therefore by adding more $$1$$s in the input, we can only increase or leave as is the number of $$1$$s in the output.

[Building account systems (2017)](https://blog.plan99.net/building-account-systems-f790bf5fdbe0) - Makes some good points about all the complexities involved in building an account system. It's not just properly hashing passwords - there's a massive amount of features to think about, interactions with external systems such as email, and big product costs (resources diverted from other projects, people not wanting to join because they don't want yet another login to remember, PR issues when a security incident happens) etc.

[Stability in a chaotic world - how Postgres makes transactions atomic (2017)](https://brandur.org/postgres-atomicity) - a deep-ish dive into the internals of Postgres and how it handles commit/rollback logic for transactions. 

[How hardware drives the shape of databases to come (2017)](https://www.nextplatform.com/2017/08/15/hardware-drives-shape-databases-come/) - a [Next Platform](https://www.nextplatform.com/) interview with [Michael Stonebraker](https://en.wikipedia.org/wiki/Michael_Stonebraker) about the next wave of databases and the hardware they're going to run on. He sees a sharp separation between OLTP and OLAP workloads, with the former moving completely to in-memory DBs, while the latter remaining on disks, but with problem specific storage, such as columnar for basic business intelligence and array for scientific and numerical work.

[An intro to compilers (2017)](https://nicoleorchard.com/blog/compilers) - I've placed this here mostly for the nice graphics. It is an introduction in the very realest sense of the word, as you won't get to say more than "Hi!" to compilers.

[Principles of sharding for relational databases (2017)](https://www.citusdata.com/blog/2017/08/09/principles-of-sharding-for-relational-databases/) - talks about sharding form a business perspective. What type of business you have, be it B2B, B2C or [B2B2C](https://www.techopedia.com/definition/23169/business-to-business-to-consumer-b2b2c) has a powerful impact on what sort of sharding you can realistically use. B2B comes out well ahead, as each client is almost completely separated from the others, making sharding by `customer_id` quite easy. On the other hand, B2C, especially in social applications such as Facebook or Twitter, makes sharding very hard, as there are a lot of connections between entities. A tight read and there's more to explore from the Citus blog as well.

[Preventing server overload: limit requests being processed (2017)](http://www.evanjones.ca/prevent-server-overload.html) - a rather rough article about approaches to managing server overload. When you can't throw extra resources at the problem very fast that is. The core idea is that one should control the number of requests being processed at a given time _and_ place incoming requests in a bounded queue which drops them quickly if it's full. Both limit tail latencies. The first makes sure that the server isn't physically overloaded by work, while the second ensure there's only so much units of work to do in a given amount of time. The idea of having the queue of requests be more explicit is one I've seen floated around in other places as well. Right now, when you use a given framework, it's kind of opaque where the request come and what control you have on them to do things like this or backpressure etc.
