---
published: true
layout: post
date: '2019-02-22 07:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #61'
---
[API gateways are going through an identity crisis (2019)](https://medium.com/solo-io/api-gateways-are-going-through-an-identity-crisis-d1d833a313d7) - I like this article especially for the nice overview of the various kinds of things which have been called "API gateways" - frontends for backends, Kubernetes access managers, API infra as a service offerings etc.

[Uber's big data platform: 100+ petabytes with minute latency (2018)](https://eng.uber.com/uber-big-data-platform/) - a look at the evolution and current status of Uber's "data systems". Crazy stuff! And also a reminder that once you reach a certain scale, there are no already-build solutions. You have to use off-the-shelf and custom stuff to make something which works for you!

[Don't get clever with login forms (2019)](http://bradfrost.com/blog/post/dont-get-clever-with-login-forms/) - a bunch of nice design patterns (as in UX design) for login forms. Biggest standout is _being linkable_. Which is something all webapps should have for their major flows. Didn't also consider that nice UX can cause issues for support people - if there's no link for the login page, it's hard for them to tell a customer where to login, for example.

[Open location code (2018)](https://github.com/google/open-location-code) - the [design doc](https://github.com/google/open-location-code/blob/master/docs/olc_definition.adoc) for the [plus codes](https://plus.codes/) which have popped up recently in Google Maps. It's really interesting looking at how such a _big problem_ got tackled, what constraints they had (making codes unambiguous, making them short, dealing with projection distorsion, dealing with scale etc..) and how they solved them. An alternative for this is [what3words](https://what3words.com/) - which has a totally different approach to this.

[I don't want to learn your garbage query language (2018)](https://erikbern.com/2018/08/30/i-dont-want-to-learn-your-garbage-query-language.html) - SQL is still the lingua franca of database interaction. And most query languages are based on it. But the author makes the point that there shouldn't be so many dumbed down variations, but instead folks should just try to provide SQL atop whatever they're trying to expose. Also, a good argument for no-ORM/micro-ORM movements.
