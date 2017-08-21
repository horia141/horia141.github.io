---
published: true
title: "History Tables"
layout: post
date: 2017-08-21 09:39
categories: post
tags: sql rdbms database history event event_sourcing
comments: true
math: false
---
Somebody recently asked on a forum I frequent what’s a way to get a history of the changes a user has made to their account.  Turns out they were building their own application, with Laravel and  basic PHP. This is a common product need and is a nice feature to boot. A common extension is to have this for all entities an application cares about.

I tried to provide an answer, but it wasn't good enough. So I decided to write a blog article about it, rather than a bigger forum post. Because this is an important issue when laying down the data architecture for any system. And in my experience it wasn't something I learned _in school_. Rather, it was something I learned on the job by looking at how people build systems.

The author implied that there might be an automatic way to get this data. It turns out there is, and we'll look at some approaches towards the end of the article. But the bulk of the article will be dealing with how to do this _by hand_. The automatic ways are _not there yet_ so you have to think about this from the get go. So it has to be a conscious design decision, rather than piggybacking on this or that low level feature.

To make things easier, let's suppose you're tasked with building something like an online book shop. Nothing fancy, but in your data modeling you'd certainly have something like a `Books` table, which is linked to tables such as `Publishers`, `Author`s etc. Classically, you might model `Books` as:

{% highlight sql %}
create table Books (
    Id serial primary key (Id),
    Title varchar(100) not null,
    Description varchar(2000) not null,
    AvailableFromPublisher bool not null
)
{% endhighlight %}

There's a small set of actions you can do on `Books` or an instance of it. You can add a new book for sale, you can change the title or description or you can mark it as available from the publisher or not. The code that does these changes is your _business logic_, and it understands the lifetime, possible states, valid values etc. for your books. The code itself can be in a classic monolithic MVC app, a REST based microservice or even something more exotic like a Thrift or gRPC based service[1]. Ideally, there won't be any other code which modifies an entity, except for the one-off migration or cleanup.
 of choice, changes occur as a result of a request from some user, and happen as one unit or _event_. So we can see the evolution in time of one entity as a series of events, each of which take the entity from one state to another, up until the current time.

The problem with a straight approach like this one is that it only reflects the _current_ state of the world. However, many times, we are interested in the whole history of event for an entity up to _right now_. And to do this, a good pattern to follow is that of _history tables_.

More precisely, for each entity we have to define two tables. One to store the actual current version of the entity, and one to store all the application-level events which affected that entity. The former is what's used in the day-to-day of the application, while the latter is used to display the history when it's needed, for debugging, for compliance etc. The model would become something like this:

{% highlight sql %}
Create table Books (
    Id serial primary key(Id),
    Title varchar(100) not null,
    Description varchar(2000) not null,
    AvailableFromPublisher bool not null
)

Create table BooksHistory (
    Id int primary key,
    BookId int not null references Books(Id),
    Timestamp datetime not null,
    Type smallint not null,
    ExtraData jsonb null
)
{% endhighlight %}

The new table logs all events which have occurred for each entity in turn. It has a reference to the entity it concerns and a timestamp for when the event happened. An index on these two columns is a good idea. I've found that keeping the order `BookId, Timestsmp` is usually the better choice, as you'll more often want to find all events for a particular book rather than all events at a particular time. But if your access patterns are more towards the latter case, definitely have it that way as well. If there might be some time between when an event “happens” and when it is recorded, you can have two timestamps instead of just one. That is, have a timestamp for when the event _happened_, and one for when it was _recorded_. The `Type` field indicates which of the limited set of actions we spoke about earlier happened. The first event will inevitably be of type `Created`, while the latter vary according to the entity. Finally, you should have a free-form column for any data that is relevant to the event. For example, the arguments supplied by the caller of an REST endpoint. I've seen people include the results of calls to external systems or other internal process state. I've also seen a diff of the old and new versions included. And I've seen the full old and new versions of the entity included as well.

Conceptually you can view the current version of the event as the result of applying the _business logic_ to the stream of events, starting at creation and continuing to the present. It is a very functional way of thinking about your database. In general, this way of thinking is one which is [gaining popularity at the backend](https://www.confluent.io/blog/turning-the-database-inside-out-with-apache-samza/), under the guise of such architectural patterns such as [event driven systems](https://www.youtube.com/watch?v=STKCRSUsyP0) or [event sourcing](https://martinfowler.com/eaaDev/EventSourcing.html), as well as on the front end, with things like [flux](http://facebook.github.io/flux/) and [redux](http://redux.js.org/) gaining prominence. Having history tables won't get you to a fancy eventful architecture, but it _is_ a good start in that direction.

Naturally, writes to the database become a bit more complex. Every mutation must be accompanied by an appropriate history event generation. The write itself must happen in a transaction, so as not to get the mutation without the event, or the event without the mutation. Though, truth be told, the latter case can be detected and corrected by reapplying the unsolved mutations in order, as long as there's no state lost.

Besides the uses that are internal to the service, events are useful for interacting with the external world as well. For example, beside adding an event to the history table, you can also publish it to a message queue for processing by downstream parties. Usually such a change is non-transactional with the main database write, so you risk losing the event at the queue if there's a failure just after the database write. But you can leave the pushing to a separate process which also keeps track of whether an event has been published or not, and retries publishing until it's accomplished.

Notice that not all tables need to be handled like this. Analytics roll up tables and OLAP-ish tables in general, auxiliary tables for entities, many-to-many tables etc don't generally need histories. Histories are something which concerns entities rather than database tables.

As I've said in the beginning, doing things _by hand_ is not the only way to go about solving this problem. Before we go, let's look at what the automatic alternatives are, and what their pros and cons are. 

The nicest setup is that where the database itself offers support for recording events or even multiple versions of the same object. This is the best way to go I think, and this is definitely something you want to leave to the database system, so it can do it more efficiently and you don't have to reimplement it so many times.

The major relational databases have started adding support for  [temporal databases](https://en.wikipedia.org/wiki/Temporal_database), which record something akin to the history of each column. This still seems work-in-progress, so don't count on your standard issue ORM having support for this just yet, but it’s a good trend. The biggest issue I see is that there's still no notion of event or cause of a change, but rather just the change itself. Also, working with them seems tricky at a first glance, since there has to be a step where one infers the events from the set of changes.

In the realm of NoSQL, [Bigtable](https://en.wikipedia.org/wiki/Bigtable) related systems like [HBase](https://hbase.apache.org/) or [Cassandra](http://cassandra.apache.org/) also allow multiple versions for a row/document. Though the idea is to keep something shorter than the full history. The same holds true for NewSQL systems like [Spanner](https://cloud.google.com/spanner).

While not yet a common feature, I expect more and more systems dedicated to OLTP workloads to allow for storing full histories.

There's other ways as well. Though [some would say death is cleaner](http://www.tzr.io/yarn-clip/dd1c6943-3d92-4d29-97ca-a3bcbd2118e4/gif). Triggers attached to mutation events on tables can create the history entries, for example. While this works, you'd get all the disadvantages of triggers and application code inside the database as well. You can also scan the change stream databases can publish. This is usually used for replication, backup or feeding into another “big system” like a data warehouse or [Kafka](https://kafka.apache.org/). However this seems particularly low-level and code intensive for something the application should do.

So there you have it. A lot of words for a fairly simple concept. Hope this was helpful.

---
[1] In which case you might actually have a service definition with clean method names for each action, rather than it being implicit in some front-end code or other changes.
