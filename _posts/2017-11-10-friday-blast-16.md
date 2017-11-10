---
published: true
layout: post
date: '2017-11-03 10:30'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #15'
---

[Tough Cookies (2017)](https://scotthelme.co.uk/tough-cookies/) - the 2017 guide to making secure cookies. They should be http only, secure, have the same site attribute and use prefixes. This protects against XSS and XSRF attacks in a first instance, as well as ensure the cookies are essentially restricted to the role of association information for user state.

[CSRF is dead (2017)](https://scotthelme.co.uk/csrf-is-dead/) - a deeper dive into the same site attribute for cookies. This works by only allowing the attachment of the given cookie to request with the same origin as the cookie. This effectively stops XSRF attacks. Browser support is quickly building, but you'll still have to use some of the old methods for a while.

[An engineers guide to cloud capacity planning (2017)](https://increment.com/cloud/an-engineers-guide-to-cloud-capacity-planning/) - the bottom line is that you shouldn't worry that much about "exact planning" and worry about having an application and infrastructure for it which can scale when it happens.

[Consistency models of cloud storage services (2016)](https://blog.cloudrail.com/compare-consistency-models-of-cloud-storage-services/) - a fun overview of the various cloud storage offerings' consistency models. Includes consumer services like DropBox or Box, for which I haven't really considered the question of consistency before.

[Web development has become weird (2016)](http://ane.github.io/2016/10/25/web-development-has-become-weird.html) - a rant against SPAs. There's some merit to it, especially about reinventing the wheel. But I do think that a properly build SPA has a superior experience to a traditional one. As well as being more interesting to build - much more like an Android or iOS app, than a "site". Some of the tech choices have sedimented as of 2017. It isn't the case anymore that there's a build system a week or package manager a month. That "boring" period the author was referring to might be coming sooner.

[Understanding HBase and BigTable (2008)](http://jimbojw.com/wiki/index.php?title=Understanding_Hbase_and_BigTable) - an older read but still relevant. It's harder to get experience with some large scale databases like HBase and BigTable, since they only come into play at a certain scale. So these sorts of articles are useful for building up some experience with them, as you never know when a job might require it. This one has a very nice and incremental way to arrive at the final HBase/BigTable data model, which might not be as intuitive for somebody coming from a relational background.
