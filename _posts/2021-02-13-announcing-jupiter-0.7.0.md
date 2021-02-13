---
layout: post
title: "Announcing Jupiter Release 0.7.0"
categories: post
date: '2021-02-13 07:00'
tags: jupiter
comments: true
---
I've prepared a major release, namely `0.7.0`. Since I think I jumped some releases, I will also summarize the
`0.6.x` releases.

Here's what's new:
* Metrics support. There's now basic support for handling metrics.
* Notion fields for inbox tasks, big plans, etc. are now in a stable order, and many of the "technical"
  ones are hidden. It leads to nicer UX for working with these entities.
* Big refactorings in the codebase. Nothing user-visible but these changes allow major work in the
  future.
* Make storage work with relative paths, and allows easy support for non-Docker operation.
* Tags for smart lists.
* An embedded notion of "done" for smart list items.
* The actionable date fully controls visibility in boards - it's not just a week before.
* Faster GC.
* Numerous bugfixes and small improvements.

As always checkout the [installation instructions](https://jupiter-goals.readthedocs.io/en/stable/install/) to find
out how to get hold of the latest version.
