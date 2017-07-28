---
published: true
title: "Friday Blast #3"
layout: post
date: 2017-07-28 22:10
categories: post
tags: friday_blast links
comments: true
math: true
---

A shorter blast this week, on account of being on vacation.

[A brief history of the UUID (2017)](https://segment.com/blog/a-brief-history-of-the-uuid/) - what I expected to be a short article about UUIDs turned into a deep dive into their long history. There's even some code archeology involved. Fun fact: telephone numbers were the first unique identifiers we used in communication.

[The best icon is a text label (2015)](https://thomasbyttebier.be/blog/the-best-icon-is-a-text-label) - and the best summary is the title itself.

[Implementing state machines in PostgreSQL (2017)](http://felixge.de/2017/07/27/implementing-state-machines-in-postgresql.html) - worth it alone for the advanced usage of Postgres, this article talks about various ways of implementing state machines directly in Postgres. More than just having a `state` column and letting application code deal with state management, that is.

[Boolean logic in polynomials (2017)](https://jeremykun.com/2017/07/24/boolean-logic-in-quadratic-polynomials/) - a neat way to encode boolean formulas as polynomials. You transform a boolean expression $$A$$ with variables $$x_1, x_2, \dots, x_n$$ into a polynomial $$A_P$$ in $$x_1, x_2, \dots, x_n$$ by turning every `AND` into multiplication and every negation of a term $$F$$ into $$1 - F_P$$. `OR` is handled by [DeMorgan's law](https://en.wikipedia.org/wiki/De_Morgan%27s_laws). There's two or three examples in the article of real-life[1] applications of this transformation as well.

---
[1] Real-life CS theory at least.
