---
published: true
layout: post
date: '2018-03-02 07:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #30'
---

[Differential privacy for dummies (2016)](https://robertovitillo.com/2016/07/29/differential-privacy-for-dummies/) - differential privacy is a way of working with data which doesn't provide information about any one person / item in the data set. A neat example is asking people to identify as criminals/drug users etc. There is a protocol of adding noise to the data, which can be done by each person being asked in turn, so that (1) you don't know if any one person is actually in the target class and (2) you can compute population queries such as total number of people in the class, proportion of people in the class etc. There's a bunch more examples there as well as a brief theoretical overview. Interesting stuff for the age of big data and big surveillance.

[SSTable and log structured Storage: LevelDB (2012)](https://www.igvita.com/2012/02/06/sstable-and-log-structured-storage-leveldb/) - we've covered [Log-structured merge-tree](https://en.wikipedia.org/wiki/Log-structured_merge-tree) here before, but mostly in the context of their use in Big Data storage engines like BigTable, HBase, Cassandra etc. [LevelDB](http://leveldb.org/) is a storage engine built with the same methods, but aimed at "small data". It's an alternative to SQLite or flat files. The article goes into some details about SSTables, which are the underlying data structure in many database engines (of the NoSQL variety at least).

[Protocol buffers, Avro, Thrift & Message Pack (2011)](https://www.igvita.com/2011/08/01/protocol-buffers-avro-thrift-messagepack/) - just a bit of commentary on the various serialization and RPC mechanisms.

[Measuring & optimizing I/O performance (2009)](https://www.igvita.com/2009/06/23/measuring-optimizing-io-performance/) - written in the age of disks, there's still a bit of interesting stuff here. Mainly around the use of `iostat`.

[Terraforming Stack Overflow Enterprise in AWS (2018)](https://medium.com/@palantir/terraforming-stack-overflow-enterprise-in-aws-47ee431e6be7) - the story of how Palantir "productionized" their install of Stack Overflow Enterprise. A nice overview of the SO architecture is included as well. If you're a big company looking for a knowledge management solution, do know that SOE exists.

[Evaluating options for Amazon's HQ2 using Stack Overflow data (2018)](https://stackoverflow.blog/2018/02/28/evaluating-options-amazons-hq2-using-stack-overflow-data/) - a data journalism article from our data team's [Julia Silge](https://stackoverflow.blog/authors/juliasilge/). Amazon is looking for a place to setup their second headquarters in the US and are running a sort of contest for cities. Much like the Olympics it seems like it's a losing proposition for cities, but they can't afford not to participate. Julia looked at technical consideration of the workforce in the 20 finalist cities to see how well they'd match the things Amazon would need.
