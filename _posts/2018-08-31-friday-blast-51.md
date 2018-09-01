---
published: true
layout: post
date: '2018-08-31 07:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #51'
---
[In defence of complicated measurement systems (2018)](https://www.johndcook.com/blog/2018/08/25/complicated-measurement/) - a really good one from John D Cook. Measurement systems are tools for humans to use - they're as good as is needed. We have (almost) uniform and concentrated systems now, but in the past the unit for measuring nautical distance was different from the one used to measure lengths of cloth. And why not? When would one interact with both during a regular lifetime?

[How SendGrid scales its email delivery systems (2018)](https://www.infoq.com/news/2018/07/sendgrid-email-scaling) - I was actually expecting some super advanced stuff here, considering the actual scale they deal with (40B messages per month). But there's actually a lot of low-tech stuff (in a bad way this time - Ceph for example), and a lot of technical debt to be paid. Glad to see a nice usage of Docker in testing though.

[Where Vim came from (2018)](https://twobithistory.org/2018/08/05/where-vim-came-from.html) - Vim has a very long history, and two bit history did a bang up job of documenting it. There's a warm and fuzzy feeling knowing that the two text editors - Vim and Emacs[1] have been worked on by some of the biggest names in computing - Ken Thompson, Dennis Ritchie, Bill Joy, Richard Stallman etc.

[M3: Uber's open source, large scale metrics platform for Prometheus (2018)](https://eng.uber.com/m3/) - there aren't that many _large scale metrics platforms_ to boot. Prometheus or OpenTSDB can only get you so far, but if you want to do something company wide (when the company is fairly large), and offer it as a service to other teams (so you're not left running your own stuff and the metrics system as well, like in the 2015s), there's not too much to choose from. The paper goes into the meat of how the system is build atop Prometheus, Etcd and others. Issues like retention polices and downsampling are also covered, which is a bit of a sore spot with the baseline components usually.

---
[1] And are there any others?
