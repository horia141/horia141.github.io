---
layout: post
title: "Jupiter Dev Log 1 - Setting Up Publishing To DockerHub"
date: 2020-02-24 07:20:05
categories: post
tags: jupiter
comments: true
---
The installation instructions were _bad_ so I had a first attempt at making a saner distribution method. Ideally Jupiter should be packaged as a Python package, a brew formula for MacOS, a deb package for Debian and derived distributions, an rpm package for RedHat and derived distributions, a docker image, etc. Once installed it should act like a regular script. So you can just `jupiter upsert-tasks` and it would work like `cat /etc/passwd`.

But I started with the Docker image cause it’s the one I’m most familiar with, and the one which seems simplest to set up. For real, all the others are quite involved! Didn’t realise this before I started reading the docs for them. Docker isn’t exactly great here, as it makes it easy to publish and manage the artifact, but relatively hard to run it locally. You’ll still need to do `docker run -it --rm --name jupiter-app -v $(pwd):/data --env TZ=Europe/Bucharest horia141/jupiter:latest …` but you’ll skip cloning, `make`ing, etc. So a partial win.

The plan was simple. First I created [public repository](https://hub.docker.com/r/horia141/jupiter) in my DockerHub account. This will be the target where the images are pushed. The next step is to add a new make `docker-push`. The `Makefile` looks like:

```make
docker-build:
    docker build -t jupiter .

docker-push:
    docker tag jupiter horia141/jupiter:latest
    docker push horia141/jupiter:latest

.PHONY: docker-build docker-push
```

To build and publish a new image you’d so something like:

```bash
$ make docker-build
$ docker login
$ make docker-push
```

Of course, the latter step can only be done by me, or by a CI/CD tool. But that’s a discussion for another blog post.
