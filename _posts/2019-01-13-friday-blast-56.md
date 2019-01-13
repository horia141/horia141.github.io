---
published: true
layout: post
date: '2019-01-13 07:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #56'
---
[16 ways to measure network effects (2018)](https://a16z.com/2018/12/13/16-metrics-network-effects/) - a company has _network effects_ when users benefit from new users coming into the platform. Think of Facebook, Twitter or Uber as canonical examples of these sorts of businesses in the tech space. This article is a rundown of no less than 16 metrics to describe such companies. Obviously useful for _insiders_, though some of these are reported by public companies as well.

[Things UNIX can do atomically (2010)](https://rcrowley.org/2010/01/06/things-unix-can-do-atomically.html) - I recently needed to do some inter-process synchronization from Java and thought about using file-system methods for locking. This turned into a goose chase of "thing I can actually" lock on, and turns out just linking and file/directory creation (in certain modes) are OK.

[Lock on existance of file in Java (2014)](https://stackoverflow.com/questions/26850724/lock-on-existence-of-file-in-java) - a SO thread where I started my search and which lead to the previous article. What I ended up using was picked up from here, namely `File.createFile`.

[A tale of two standards (2005)](https://www.samba.org/samba/news/articles/low_point/tale_two_stds_os2.html) - a comparison of POSIX and the Win32 files API. I kind of missed the boat on Windows as a target for programs, so I have only the fuzziest knowledge of what it is all about. Save for ASP.NET work, which is far removed from anything system level. So I'm always impressed at the tech chops of the folks who built the system, and the somewhat unwarranted flak the business side has drawn on the solid technology part. Still reading on locking at this point.

[Addendum on the Brokenness of File Locking](http://0pointer.de/blog/projects/locking2) - more woes of file-locking. But in the presence of NFS. Which we _all knew_ was kind of borked to begin with, cause it couldn't offer POSIX compliance well. OTOH, you never know if the disk you're writing to is a local or remote one in some cloud providers. So "this won't happen to me" is not a valid excuse to try the file locking in POSIX.
