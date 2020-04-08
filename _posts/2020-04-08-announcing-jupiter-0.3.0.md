---
layout: post
title: "Announcing Jupiter Release 0.3.0"
date: 2020-04-08 07:20:05
categories: post
tags: jupiter
comments: true
---
Today marks the date of the third "minor" release of Jupiter - version `0.3.0`. It's a really big release, as it
essentially moves all the recurring tasks interactions to be in the "new way", like vacations or workspaces.

More precisely there is a major overhaul of interaction with projects and recurring tasks. Basically, there's no
more working directly with YAML files. Instead, there are CLI commands and Notion boards dedicated for this, much
like there are for vacations. Checkout the [concepts page](https://jupiter-goals.readthedocs.io/en/stable/concepts)
for an up-to-date view of all that's possible now.

An extract from the [tutorial](https://jupiter-goals.readthedocs.io/en/stable/tutorial/) - to create a project you
need to run the `project-create` command, like so:

```bash
$ docker run \
    -it --rm --name jupiter-app -v $(pwd):/data --env TZ=Europe/Bucharest \
    horia141/jupiter:latest project-create \
        my-work \
        --name "My Work"
[ Some output here ]
$ git add .
$ git commit -a -m "Created project 'My Work'"
```

Contrast this to the previous approach, where you had to create and edit a complex YAML file, and then run
some command on it and hope it works.

There are big plans and inbox tasks which are still left to do (so more than half the work), but after that the
system will have taken a really nice shape - enough for a `1.0.0` version.

A small but useful feature is the ability to suspend recurring tasks. While suspended, no new instances will be
generated for them. This allows folks to gracefully handle situations when a habit or chore can't be done, due to
external factors, for example. This feature is obviously inspired by the Coronavirus situation.
