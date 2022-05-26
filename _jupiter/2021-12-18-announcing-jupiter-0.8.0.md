---
layout: post
title: "Announcing Jupiter Release 0.8.0"
categories: post
date: '2021-12-17 07:00'
tags: jupiter
comments: true
---
I've prepared a major release, namely `0.8.0`. This is just the second release of the year, and the first in
more than 10 months.

It has some major additions, speed improvements, bugfixes. And also a major rearchitecting of the system. No
line was left untouched! Hence the big delay.

Here's what's new:
* Added support for a "personal relationship manager" feature. Read more in the [PRM section](https://jupiter-goals.readthedocs.io/en/stable/concepts/prm/).
* Entities which can be associated with a project, can now use a default project.
* Faster local -> Notion updates
* Moved some entities to SQLite storage from the text based one. It's faster and safer.
* Stopped syncing archived inbox tasks
* A massive refactoring of the code-base. Nothing was left untouched. The new code is
  easier to maintain and structurally better organized.
* Fixed high severity security issue with a `mkdocs` dependency
* Bugfix of metric entry sync which would clear the collection time on Notion side
* Bugfix of recurring task sync start date value being ignored if set on Notion side
* Bugfix of not syncing vacations sometimes


As always checkout the [installation instructions](https://jupiter-goals.readthedocs.io/en/stable/install/) to find
out how to get hold of the latest version.
