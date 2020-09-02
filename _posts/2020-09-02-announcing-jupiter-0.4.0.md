---
layout: post
title: "Announcing Jupiter Release 0.4.0"
date: 2020-09-02 07:20:05
categories: post
tags: jupiter
comments: true
---
Today marks the date of the fourth "minor" release of Jupiter - version `0.4.2`. It's a massive release, and the last
one I'll make this massive! It literally has tens of big changes, and took about 5 months to deliver! Not cool for
such a small project.

Checkout the [release notes](https://jupiter-goals.readthedocs.io/en/stable/releases/version-0.4.2/) for the full info.

I'll summarize the changes here though:

* Brand new and expanded [docs](https://jupiter-goals.readthedocs.io/). More stuff to come here!
* Massive rethink of the way storage is handled - new format is simpler and more robust.
* Added the ability to build [reports](https://jupiter-goals.readthedocs.io/en/stable/concepts/reporting) for past
 activity.
* Made a unified `sync` [command](https://jupiter-goals.readthedocs.io/en/stable/concepts/notion-local-sync) instead of the various per-entity ones.
* Add a single `gc` [command](https://jupiter-goals.readthedocs.io/en/stable/concepts/garbage-collection) for clearing up stuff on Notion-side.
* Added commands to _hard remove_ entities from both [local storage](https://jupiter-goals.readthedocs.io/en/stable/concepts/local-storage) and Notion.
* Added the _timezone_ as a workspace-level setting.
* Introduced the concepts of _chores_ and _habits_. A recurring task can be one of these, and they'll get slightly
  different treatment when building reports, for example.
* Got rid of the _group_ property for recurring tasks.
* Helpful error links to the "How Tos" section on certain errors.
* A `--version` argument to the [CLI](https://jupiter-goals.readthedocs.io/en/stable/concepts/jupiter-cli).
* Added type annotations to the whole codebase.
* Removed the `--dry-run` argument to certain commands.
* Added many log messages, and added the ability to control the log levels shown, as well as a general `--verbose` flag.
* Upgrade to Python `3.8.5`.
* Many bugfixes and performance improvements.

