---
published: true
layout: post
date: '2017-09-22 18:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #10'
---

This is the 10th installment of the Friday Blast series. I missed last week on account of explosive health problems. So today's dosage is a little bit larger than the usual. Enjoy!

[What every software engineer should know about search (2017)](https://medium.com/startup-grind/what-every-software-engineer-should-know-about-search-27d1df99f80d) - a longer read about setting up search for a web application. Think the search in Kayak, Booking, AirBnB, rather than a vanilla document search one might encounter on a blog. The underlying theme is that it is a _hard_ and _not yet solved_ problem. Solving it requires a dedicated team and dedicated systems, and a lot of customization. Even with off-the-shelf solutions like [ElasticSearch](https://www.elastic.co/).

[Do not let your CDN betray you - use subresource integrity (2017)](https://hacks.mozilla.org/2015/09/subresource-integrity-in-firefox-43/) - subresource integrity is a very cheap way to add a serious security boost to your webapp. It aims to check that the resources requested are actually the ones you want in a setting where some of them might come off a CDN or other third-party you don't fully trust. You just need to add an `integrity` attribute to your `script` and `link`s, which contains a hash of the file's expected content. If whatever the browser downloads has a different hash, the resource will be blocked from loading in the page. The main page needs to be served from your own systems of course, and anybody who can MITM that can remove the integrity checks, but you've got bigger problems by that point.

[The ultimate guide to CMS - part 1 (2016)](https://www.webdesignerdepot.com/2016/11/the-ultimate-guide-to-cmss-part-one/) and [part 2](https://www.webdesignerdepot.com/2016/12/the-ultimate-guide-to-cms-part-2/) - an overview of the field of [CMSes](https://en.wikipedia.org/wiki/Content_management_system) - one of the most common types of web applications (and applications in general) out there.

[std::visit is everything wrong with modern C++ (2017)](https://bitbashing.io/std-visit.html) - this is one of the reasons I've left C++ development. There were certain tasks which seemed easy to solve, but which required a deep mastery of templates and features. That and [trigraphs](https://en.wikipedia.org/wiki/Digraphs_and_trigraphs). Entertaining for the high-power C++ though.

[What's so bad about POSIX I/O (2017)](https://www.nextplatform.com/2017/09/11/whats-bad-posix-io/) - for high-performance computing the problem seems to be the rather strong consistency model POSIX dictates for reads and writes. On a local machine it's easy to guarantee that if you write to a file from a process, later reads from other processes would see the write. Regardless of layers of caching or other optimizations employed by the OS. This thing is quite expensive to provide in a distributed environment, and for many applications it's not needed. The article focuses on solutions that have been proposed for this problem.

[Locality sensitive hashing by Spark (2016) #talk](https://www.youtube.com/watch?v=Ha7_Vf2eZvQ&feature=youtu.be) - how Uber built a distributed duplicate ride detection system based on [Locality Sensitive Hashing](https://en.wikipedia.org/wiki/Locality-sensitive_hashinge). LSH is a hashing scheme which tries to map "similar" objects, according to a similarity metric, to the same hash bucket. So the opposite of a regular hashs, used in lookups. This means that similar objects will be grouped together, and the $$O(N^2)$$ similarity computation can be reduced to a much smaller bunch.

[Unlearing descriptive statistics (2017)](http://debrouwere.org/2017/02/01/unlearning-descriptive-statistics/) - it's well known that many of the statistical measures of centrality, spread, skew, correlation etc. aren't really all that useful for real-world datasets. Rather, they're good for Gaussian data and analyzing them is OK mathematically. The article discusses this issue at length, providing examples and alternatives.

[How Dropbox securely stores your passwords (2016)](https://blogs.dropbox.com/tech/2016/09/how-dropbox-securely-stores-your-passwords/) - a look into how Dropbox stores passwords. There's a lot of defense in depth here. Passwords are of course stored with `bcrypt` with a per-user salt. But there's also something called a _global pepper_, which is a hard-to-get value used to encrypt the hashed passwords. Their plan is to store this pepper in a secure hardware module of their servers.

[Quantifying the information content of personal data (2017)](https://www.johndcook.com/blog/2017/09/12/quantifying-the-information-content-of-personal-data/) - the article is a back-of-the-envelope computation of the bits of information obtain from various pieces of personal data - gender, zip-code, age etc. It's neat that knowing somebody's age and post-code is enough to identify that person, when the age is particularly high.
