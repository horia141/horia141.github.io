---
layout: post
title: "Announcing Jupiter Release 0.1.0"
date: 2020-03-15 07:20:05
categories: post
tags: jupiter
comments: true
---
Today marks the date of the first "minor" release of Jupiter - version `0.1.0`. The main improvement is a switch to a
command or Notion only flow for workspace and vacations. No more mucking about in `yaml` files. Instead everything can
be done via the `jupiter` CLI app or via Notion.

Here's a sneak peak of the new flow for dealing with vacations:

![Vacations demo](/assets/jupiter-demo-vacations.gif)

Working more the tool and showing it to various friends and colleagues has really highlighted the clunkiness of the
current approach. So I set out to rethink a bit how this interaction would go. Three things stuck out. First, editing
`yaml` files is a bad UX. Second, editing `yaml` files and maintaing an ill-specified schema for them is a _horrible_
UX. Third, there should be an idea of equivalence between Notion and the `jupiter` CLI app - to allow easier
interaction on the one side, and to allow for independence and flexibility on the other side.

The results is a natural flow. The `yaml` files are an implementation detail and directly interacting with them will
gradually be phased out. Instead `jupiter` CLI commands operating on them (and on Notion), or Notion actions (which
need to be synced back to the local store) will take their place. For now, workspace and vacations interactions are
totally replaced.

For workspace interactions, creating a `user.yaml` file is replaced with the `jupiter ws-init` command. There are also
`jupiter ws-set-name`, `jupiter ws-set-token`, and `jupiter ws-sync` commands added to cover changing names, changing
the Notion access token, and syncing back any Notion-side changes to the local storage. There isn't a 
`jupiter ws-set-space-id` command, because that thing _should not be editable_. A small win for UX. The name can be
change via Notion too, by simply editing the name of the root page.

For vacations interactions, editing the `user.yaml` file is replaced with the `jupiter vacations-add` and 
`jupiter vacations-remove` commands. There are also `vacations-set-name`, `vacations-set-start-date` and 
`vacations-set-end-date` commands with predictable semantics. Finally, a `jupiter vacations-sync` command makes sure
Notion and the local storage are synchronised, by adding vacations from one not found in another. On Notion side, you
just have a spreadsheet like view of all the vacations, and can add/edit/remove them in-place. A single call to
`vacations-sync` is needed at the end to make everything synced.

That's it for this release announcement. I'll be working a bit next on some quality control, namely linting and
testing and their integration into the CI flow, and I'll probably blog a bit about that too. I'll also be looking at
a better way to publish the documentation. After that, I'll return to more _feature_ work and try to migrate the
project interactions and recurring tasks actions. Be sure to checkout the 
[release notes](https://github.com/horia141/jupiter/blob/develop/docs/releases/version-0.1.0.md), and the new
[tutorial](https://github.com/horia141/jupiter/blob/develop/docs/tutorial.md), and the revised 
concepts](https://github.com/horia141/jupiter/blob/develop/docs/concepts.md) page.
