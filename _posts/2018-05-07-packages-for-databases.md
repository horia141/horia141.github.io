---
published: true
title: "Packages For Databases"
layout: post
sdate: 2018-05-07 15:00:05
categories: post
tags: databases distributed_systems package software_engineering
comments: true
math: false
---

A common rule of thumb in internet companies when dealing with relational databases is to avoid _stored procedures_. There’s a bunch of reasons _why_ this is, but it’s usually a combination of perceived performance issues and simply being hard to use.

The former seems to me to be a bit of programmer folklore. There’s no intrinsic reasons why it would be like that. Indeed moving code to data is a principle well used in many other systems such as MapReduce, Hadoop and their various offshoots. Indeed, many _older systems_ did exhibit bad performance, but things have moved a massive amount in the right direction in both software quality and hardware power.

The latter issue however has a grain of truth in it. Which is perhaps the understatement of the year. Working with stored procedures or any other “programmability” features of relational databases is a pain. The language itself isn’t that great to boot and the tooling around it sucks. The root of this suckage is, in my experience, the fact that interaction with the database is mainly done via interactive queries such as `CREATE PROCEDURE` or `ALTER PROCEDURE`.

One immediate issue is that rollbacks are very hard. You basically need to issue another `CREATE PROCEDURE` but with the old form of the code if you can find it in one piece somewhere. Another issue is related to the fact that many teams use a migration tool and store migration scripts in source control. This might be OK for schema-level changes[1] but it’s a pain for stored procedures which are usually larger chunks of code. Changes to a stored procedure are usually one migration script which fully replaces the current version of it. So diffs and other comparisons between the old and new ones are very hard to do in this context.

A final issue cuts a bit deeper. Because there’s the code and there’s the deployment of the code, and they should be independent things ideally. And with the current system there’s a very strong coupling between the two - the command for updating a procedure literally requires all the code to be specified inline!

But it doesn’t have to hurt this way and there’s a precedent for things getting better. I’m talking of course about the compute component of _internet applications_. In the last ten years we’ve moved from VPSs to PaaSes, Kubernetes and serverless and most people agree this is a good thing. And the whole infrastructure around building and deploying _code_ has evolved as well. So much so that even if the scale of the systems we’re dealing with might dwarf that of years gone by, actually interacting with them as a developer is much easier these days.

Let’s consider a bunch of examples. On one end of the spectrum, people still rent a VPS and then manually SSH into it and copy local files in order to make a deployment, like they did in “olden times”. Sometimes a script or three might be involved, but the process is very basic and direct that way. On the other end of the spectrum, you have well developed and automated code deployment pipelines, package repositories, rollout managers etc. Whole systems for managing other systems if you will. These days it’s not really even an issue of evolving from one to the other _as you get big_ or as the need arises because you can start any project regardless of size with a host of advanced tools, and get a ton of benefits.

My take is that database interactions are at the SSH and file copy end. And we’d ideally would like them to be in the opposite end.

Now the nice thing is that if you squint hard enough, databases and compute components are quite similar - both allow user-specified code to be executed. In the latter case to interact with other services or databases, while in the former to interact with the data itself. And since what works for the goose, works for the gander, we can try to emulate the developments in compute to jump start database ones.

So one concept which is useful is that of a _package_. Stored procedures or, perhaps more generally, any non-DDL query can be grouped into these packages. Databases can then load a package and make them available to users of the database. A _build process_ will take in code from a repository, run tests and produce a package. Naturally packages will be versioned and they could be stored in a repository. This function could be fulfilled by the database server itself in smaller installations or could be a separate system in larger ones.  Deployment would just push a certain package version to a group of machines and tell them to do what’s needed in order to use them. For compute nodes this is usually a restart of the node, but that’s probably overkill for storage layer applications. The set of database instances would act like something akin to a Kubernetes cluster, or PaaS system like AppEngine or Heroku. Issues like rollback or smart strategies for distributed deploy become much easier to manage and reason about.

At the source code level, we could do away with _migrations_ for these sorts of things, and hold the code just like we would any other source file. We’d get nice diffs and a real sense of progress via source control.

I’ve spoken about relational databases so far. But this issues isn’t limited to them. To the extent that NoSQL or NewSQL databases have implemented programability features, they’ve copied what relational databases had, and therefore inherited their limitations and awkwardness.

Anyway this is the big idea. At this point in the article I should plug my side project or product which provides all of the above and more for Postgres/MySQL/SQL Server. But there’s no such thing yet or for the foreseeable future. It’s just my wishful thinking. But I do think it’s a neat idea and if you want to run away with it and actually build something you’d have a first user in me.

---
[1] Though this approach has always felt like a compromise to me. And why is it that we’re moving as an industry towards infrastructure as code and are happy to let `terraform` manage transforming a declarative description of the infrastructure into actual cloud provider commands, but we don’t want the same for schemas? Perhaps it’s time for _schema as code_?
