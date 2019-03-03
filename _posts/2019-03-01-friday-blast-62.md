---
published: true
layout: post
date: '2019-03-01 07:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #62'
---
[Multi-cloud is a trap (2018)](https://bravenewgeek.com/multi-cloud-is-a-trap/) - a case for avoiding the pitfall of designing a system for "multiple clouds". This is one in a bunch of "avoid generalisation" advice. The one I hold dear is avoid designing a system to be database agnostic. Instead, use the DB you've selected to the maximum of it's potential - which will push you naturally in the areas where it's differentiated from the others.

[Transactional data operations in PostgreSQL using common table expressions (2018)](https://rob.conery.io/2018/08/13/transactional-data-operations-in-postgresql-using-common-table-expressions/) - linked to that one, Postgres supports CTEs, which allows you to specify some nifty business logic-like operations in a single query. In general it's not a good idea to embed this logic in it, but if it's (1) in a SoA setting where only one service will have access to the DB and (2) the queries are under the control of the app, then why not?

[What's in a production web application (2018)](https://stephenmann.io/post/whats-in-a-production-web-application/) - an overview of "generic web application" architecture as of 2017-2018. The kind of stuff that'll go a long way operationally as well. OTOH, and related to a common rant of mine here, if the architecture is so _standard_, why are we building it for each app? Why isn't anybody offering something like that which should handle _most_ prod cases as an PaaS?

[The supply side of marketplaces is kind (2017)](https://andrewchen.co/why-uber-for-x-failed/) - older read but interesting one. Basically a "platform company" - think Uber, AirBnB, Taxify etc - is a success or not depending on how well they can provide for their "drivers/hosts/restaurants/etc". If they're happy, clients _will come_. If the setup is such that it doesn't work out for the first group - like when you can only offer income in a certain time of day or a certain period of the year, things are gonna be tricky.

[Don't let the internet dupe you, event sourcing is hard (2019)](https://chriskiehl.com/article/event-sourcing-is-hard) - a bunch of "real world" issues with "event sourcing" or log based application architectures. They're stuff I ran into in lower-scale log based systems, where only parts of the system are using this approach, while the others are traditional. So it's interesting that taking it to 11 doesn't solve the problems. In other words it's not just an impedance mismatch issue - it's something inherent in the approach. But then again, handling complex data sets with multiple applications accessing them is always hard.
