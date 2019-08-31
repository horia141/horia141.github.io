---
published: true
layout: post
date: '2019-08-30 07:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #77'
---
[Marking the end of pixel trackers in Basecamp emails (2019)](https://m.signalvnoise.com/marking-the-end-of-pixel-trackers-in-basecamp-emails/) - pixel tracking in emails is a common technique for gathering analytics for the emails you send. They work by embedding an image url (historically a 1x1 pixel) into the email, with some unique coordinates. When the email gets rendered, the image gets requested and you know the email was seen. They're pretty ingenious. But also a hack for tracking folks when you perhaps should not. So it's refreshing to see Basecamp take the lead here and do something against the grain of pervasive tracking which is the norm in products nowadays.

[The ARPUs of the big four dwarf everybody else (2019)](https://mondaynote.com/the-arpus-of-the-big-four-dwarf-everybody-else-e5b02a579ed3) - Amazon leads the pack here, but they're a retailer so it makes sense. What was interesting was how much Facebook dominates the advertising spend growth of the last couple of years. Also interesting that for Google, 20$/month would be enough as a subscription. Perhaps not enough for search, but for YouTube, docs, calendar etc? Sounds compelling for sure! Wonder why they're not offering this.

[Font fingerprinting (2019)](https://www.johndcook.com/blog/2019/02/04/font-fingerprinting/) - a "neat" form of cookieless tracking is font fingerprinting - figuring out the details of what fonts are installed on a computer. Unique enough to reliably track folks.

[Apache Spark at scale at Uber (2019)](https://eng.uber.com/uscs-apache-spark/) - details around the platform that Uber has built around Apache Spark in order to allow folks to easily build jobs accessing all of Uber's data. Something very similar (though at a smaller scale), we're building in Bolt too.
