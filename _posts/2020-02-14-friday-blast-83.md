---
published: true
layout: post
date: '2020-02-14 07:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #83'
---
I can't believe I haven't posted any Friday Blast in 2020 yet! It's been a bit of a hectic start of the year, but I've definitely done some reading. Time to give back!

[Give me back my monolith (2019)](http://www.craigkerstiens.com/2019/03/13/give-me-back-my-monolith/) - a plea for simple architectures. Monoliths might not be "sexy", but they're definitely the right tool up until a team grows _big enough_ and _experienced enough_ in DevOps to properly handle microservices, streaming architectures, etc.

[Managing Uber's data workflows at scale (2019)](https://eng.uber.com/managing-data-workflows-at-scale/) - every company of a certain size starts having data analysis jobs, ETL jobs, reporting scripts, etc. running along-side their regular services. Once you get enough of these, you start to see the need to organise their execution. This is where workflow services come in. Apache Airflow is a good example of an Open Source tool like this. Here is Uber's, designed for much bigger scale, and "as a service" to boot.

[Don't believe these 5 myths about the big bang (2020)](https://www.forbes.com/sites/startswithabang/2020/02/06/the-top-5-myths-you-probably-believe-about-the-big-bang/#238733992694) - turns out the little I thought I knew was wrong.

[Design principles for mathematical engineering in experimentation platform at Netflix (2019)](https://netflixtechblog.com/design-principles-for-mathematical-engineering-in-experimentation-platform-15b3ea143b1f) - Netflix has quite the big team working on their experiments platform - enough to justify a Director overseeing it! It also turns out they have a lot of custom made stats code - linear algebra, regressions, etc. Interesting that they don't use the primitives offered by Python and R for this.

[Make resilient Go net/http servers using timeouts, deadlines and context cancellation (2020)](https://ieftimov.com/post/make-resilient-golang-net-http-servers-using-timeouts-deadlines-context-cancellation/) - this is another one in a series about structured concurrency (checkout previous Friday Blasts for some links). This time in Go, and covering timeouts, deadlines (which are different from timeouts, and act like "global timeouts" sort-of), and contexts passed around services.

[Walking with atoms - chemical bond making and breaking in action (2020)](https://www.eurekalert.org/pub_releases/2020-01/uon-wwa010720.php) - this is a neat video of a molecule "walking" in a crystal lattice, and how the bonds between the atoms form and break.
