---
published: true
layout: post
date: '2018-07-13 07:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #46'
---
[Why Kubernetes is the new application server (2018)](https://developers.redhat.com/blog/2018/06/28/why-kubernetes-is-the-new-application-server/) - a case for K8s as the new "enterprisey" thing to build applications against. From RedHat, makes or JBoss and other enterprisey things (and some not-so-enterprisey things as well).

[How we built Uber engineering's highest query per second service using Go (2018)](https://eng.uber.com/go-geofence/) - an interesting read about the _geofence_ service inside Uber. The numbers are quite impressive - 100K QPS is tremendous. Sure, it's all in-memory serving, but even like that Go's performance is stellar. Interesting that only basic locking was used to build the thing, cause the team found more advanced methods were complex and not needed.

[How not to structure your database-backed web applications (2018)](https://blog.acolyer.org/2018/06/28/how-_not_-to-structure-your-database-backed-web-applications-a-study-of-performance-bugs-in-the-wild/) - the Morning Paper review of a paper by [Yang et al](https://hyperloop-rails.github.io/220-HowNotStructure.pdf). The main bit is about how massive performance gains can be had by small tweaks in the ORMs are used by programmers. The median fix they applied was just 5 lines. I think the hardness of getting these things right is one of the reasons micro ORMs like Dapper or Knex are popular.

[For more and more people, work appears to serve no purpose (2018)](https://news.ycombinator.com/item?id=17260911) - A HackerNews discussion on an interesting article in the New Yorker. Both are worth the read. My take is that we're going to see a lot of automation in the future, and bullshit jobs or minimum income schemes would be the two realistic ways forward which don't result in outright dystopias.

[Your progress as a programmer is all up to you (2014)](http://thecodist.com/article/your_progress_as_a_programmer_is_all_up_to_you) - wise words. Employers, colleagues, clients, professional associations etc. won't care about your future. But our is an industry which is very unforgiving to folks who haven't kept current. But then again, most professions are like that. Medicine, the law etc. don't stand still.
