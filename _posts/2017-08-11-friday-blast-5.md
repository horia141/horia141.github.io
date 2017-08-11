---
published: true
title: "Friday Blast #5"
layout: post
date: 2017-08-11 10:39
categories: post
tags: friday_blast links
comments: true
math: false
---

A lighter week for this issue.

[Where Tcl and Tk went wrong (2014)](https://journal.dedasys.com/2010/03/30/where-tcl-and-tk-went-wrong/) - an interesting read about an interesting language. Tcl was the first dynamic/scripting/etc language I used in a _production_ setting. It's a very elegant one, similar to Lips, and it's a shame it hasn't caught on more. The author goes into some details about the economic and "political" issues which led to the language's demise. Standing out I think is a failure of the language design team to choose either the _batteries included_ approach of Python, Ruby etc. or the _embedebble language_ approach of Lua, JavaScript etc.

[The rise of test impact analysis (2017)](https://martinfowler.com/articles/rise-test-impact-analysis.html) - talks about advanced ways of running tests. Test Impact Analysis tries to figure out which tests would be affected by a certain set of changes, and only runs those. The idea is to speed up the testing phase, for cases where there's a large burden of tests.

[The infrastructure behind Twitter (2017)](https://blog.twitter.com/engineering/en_us/topics/infrastructure/2017/the-infrastructure-behind-twitter-scale.html) - very high-level overview of the infrastructure systems used at Twitter. I found the graphs with the percentages of machines dedicated to certain tasks interesting. Otherwise there's a lot of pointers to the interesting tools Twitter has put out.

[Jeff Dean's lecture for YC AI (2017)](http://blog.ycombinator.com/jeff-deans-lecture-for-yc-ai/?src=hn) - interesting mostly because Jeff Dean. Otherwise it's an overview of what the Google Brain team has been up to these last few years. It's quite impressive, but there isn't that much to take away other than _more machines help_.

[Damn cool algorithms: log structured storage (2009)](http://blog.notdot.net/2009/12/Damn-Cool-Algorithms-Log-structured-storage) - an alternative to storing a B-Tree and write ahead log for storage engines. It's also a close relative of [Log structured merge trees](https://en.wikipedia.org/wiki/Log-structured_merge-tree), of BigTable and HBase fame. The idea is similar to that of an in-memory persistent data structure. Instead of modifying data in-place, you create new versions of it, and update the indexing structure to reflect that. In the case of disks, you need to organize the whole process through a log structure, so you have to worry about copies and memory consumption a bit more.

[Log structured merge trees (2015)](http://www.benstopford.com/2015/02/14/log-structured-merge-trees/) - a presentation on how log structured merge trees work. These is an alternative data structure to B-Trees & their friends for usage in database systems. BigTable, HBase, MongoDB etc all use or can use them. Whereas B-Trees organize data as a tree, which requires a bunch of writes for every mutation, thereby providing a limited write throughput, LSM trees organize data as a series of files, chronologically arranged. Inside each file, the data is sorted by primary key. Writes first go to a in-memory sorted tree and a secondary WAL. But once this gets too big, it is flushed to disk as another of these files. Write throughput is large, as each mutation corresponds to a single write (in the WAL). A read first checks the in-memory tree, then each file in reverse order. The check for a file is quite fast, as there's just a binary search to do. But since many files could be checked, it is heavier than a read. Periodic compaction needs to happen in order to keep the file set small. Read throughput is not that great even with compaction, in principle, but large memory caches for reads largely alleviate the problem. The article is well worth a read, and contains extensions and pointers to relevant literature.
