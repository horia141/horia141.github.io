---
layout: post
title: "When To Join A Company For Maximum Engineering Challenge"
date: 2018-01-18 10:00:05
categories: post
tags: career_advice career
comments: true
---

Disclaimer: this is a post with a bit of _career advice_. I haven't written about this at all before. And I haven't _thought_ about it that much to boot. So take whatever follows with a grain of salt. I do think the things I'm going to say are uncontroversial though, but if I'm off the mark I'd sure like to know. So any comments and critiques are welcome.

I recently saw a recording from RedisConf17 called ["Geospatial Indexing: 10 Million QPS Redis Architecture Powering Lyft"](https://www.youtube.com/watch?v=cSFWlF96Sds). That's an impressive title. And the engineering work presented by the speaker matches it. The takeaway is that they built a lot of extra stuff on top of Redis to get the system they wanted to have. Some of it was for their project, some was integration with other Lyft systems. But there wasn't anything off the shelf they could use, so they had to roll their sleeves and build themselves.

And as an engineer, that's the kind of stuff to cut your teeth on. The experience you can't get from a book or technical paper, but one you have to live. The hard engineering challenges which leave you with war stories, lessons learned and loads of bruises.

As I see it there's three phases in the development of a tech company. There's the startup phase, the growing phase and the stable/mature phase. Each has its interesting bits and its challenges and rewards. The startup phase is that murky period where you're banding on a prototype/MVP, everything is in flux, you get your first users, everybody's doing everything and you're just trying to keep the thing afloat. As the product gets more traction, you switch into the growing phase. There's more employees now and more specialization. The processes are a bit more thought out as well. Finally, the stable/mature phase is the last. Things have stabilised, there's a lot of specialization and tighter processes.

The best time to join a company, from the point of view of maximizing the chances you'll get to work on interesting stuff is the growing phase. In the startup phase, you're more likely to use off-the-shelf components and well known architectures and processes. There's still a lot of interesting stuff to do, but it's more around executing a basic solution competently than anything in particular. So we're talking about making sure passwords aren't vulnerable, or the cloud infrastructure is setup correctly. Conversely, in the mature phase, there's going to be a lot of custom tooling and large scale problems to work on, but any work that's done is going to be in the context of improving those. Much like with the product itself.

However, in the middle growing phase, there's a unique combination of factors which allow for some pretty interesting technical work. First, the scale of the problems the company is working with is going to grow. More users means more data, more things happening and more things to process. Second, the initially selected tools will start to show their limitations. The central database with replication might be too slow, or that batch Hadoop job will become unwieldy and take too long. Third, the particular idiosyncrasies of the company's business domain will become critical issues for the off-the-shelf tools. For a transportation or mapping company, GIS features will be important. For a social company, graph features will take priority etc. And those will need to be tackled with some custom work for sure. Fourth, and perhaps most importantly, there's an immediate _business need_ to solving these issues somehow. So, in the middle phase, engineers can _get away_ with a lot of things they wouldn't be able to in the first and third ones, because both "management's" and their incentives are aligned.

Now, not every company will have the particular growth path. B2C ones in the tech space are probably the safest bet. Though even for those the bar for moving to custom solutions keeps getting higher and higher. At StackOverflow for example the tech stack is famously conservative, even though the number of users is quite large (all developers basically and then some).

This isn't a clear cut rule, of course. There's plenty of interesting work in the early or late stages of any company's life, when you look at the whole ecosystems. The more cutting edge the startup, the more this is the case in the early days. Things like AR/VR or biotech startups are like that. Similarly, if a company has a solid engineering culture, there's going to be enough interesting technical work in the later stages, and not just maintenance work. But we're talking about maximizing chances here.

Also, as a final disclaimer, getting to work on interesting stuff isn't the only thing which matters for a job. Compensation, benefits, quality of life in the city or area, company culture/mission, colleagues etc. all matter in different proportions to different people. These will affect job decisions as much if not more than just technical aspects.
