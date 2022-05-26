---
layout: post
title: "Jupiter Dev Log 2 - Release Process With GitHub Actions And GitFlow"
date: 2020-03-01 07:20:05
categories: post
tags: jupiter
comments: true
series: "Jupiter Dev Log"
---
This latest instalment in the Jupiter Dev Log series covers the newly added “automatic release process” in some detail. The release process was decidedly manual before this work. I ran `make docker-push` on my local machine, and a new Docker image replaced the one on Docker Hub. There are in fact two key improvements:  having versioned releases (and a versioning process to boot), and having an automated release process which acts on some pushes to GitHub and uploads the current version to DockerHub.

The version of the code spoken about in this release can be found under the [v0.0.2 tag](https://github.com/horia141/jupiter/tree/v0.0.2) on GitHub. It’s not radically different than what was before it, however. But I’ll walk through the _thought process_ here.

The first thing that was needed was a way to decouple the push to Docker Hub from my local machine state and my login status to Docker Hub. This is achieved via [access tokens](https://www.docker.com/blog/docker-hub-new-personal-access-tokens/) which are essentially alternatives to the one password for the account. But they can be managed much better than the password - issues for a single use case, revoked, etc.

The manual release process described in the [previous article](https://dev.to/horia141/jupiter-dev-log-1-setting-up-publishing-to-dockerhub-1f1l) like so:

```bash
$ make docker-build
$ docker login
$ make docker-push
```

Can now become:

```bash
$ make docker-build
$ echo MY_TOKEN | docker login --username horia141 --password-stdin
$ make docker-push
```

The second thing I did was set up a very simple GitHub Actions workflow to essentially automatically run the above on every push to a branch.

> I chose GitHub Actions for convenience’s sake. It _looks_ quite fully featured, but I didn’t really do that much of a comparison between Travis, Circle, any other hosted CI/CD tool, and it. Self-hosted was out of the question of course, but the others _could_ have been better. Or at least Circle, cause it seemed to be innovating a bit with its orbs repositories. I knew Travis wasn’t what it used to be, but I used it a lot in the past and was familiar with it. That said it was a neat tool to learn, and seems to be pretty powerful - especially the ability to have multiple workflows, actions modularity, etc.

I setup a [secret](https://help.github.com/en/actions/configuring-and-managing-workflows/creating-and-storing-encrypted-secrets) named `DOCKERHUB_TOKEN` to the repo in GitHub. After that I added the following workflow under `.github/workflows/release.yml`:

```yaml
name: Release

on: [push]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - uses: actions/checkout@v2
    - name: Build the docker image
      run: make docker-build
    - name: Publish the docker image
      run: |
        echo ${{ secrets.DOCKERHUB_TOKEN }} | docker login --username horia141 --password-stdin
        make docker-push
```

The bulk of the work is actually done with this setup. However, it’s a bit aggressive when it does a release. More precisely:
There’s only one version - latest, with no notion of “release version”.
We really don’t want every push to any branch to be a “release”. We want some control of what gets exposed to people.

We can tackle both via process. Namely, we’re gonna implement something like [gitflow](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow) for this thing, and a small setup for storing the version and other global variables.

I added the following `Config` file to the root of the repo:

```
BASENAME=jupiter
VERSION=0.0.1
DOCKERHUB_USER=horia141
```

The `Makefile` can be evolved a little bit to reference the `Config` file via the `include & export` commands, but mostly stays the same:

```Makefile
include Config
export

docker-build:
    docker build -t jupiter .

docker-push:
    docker login --username=${DOCKERHUB_USER} --password-stdin
    docker tag jupiter ${DOCKERHUB_USER}/${BASENAME}:${VERSION}
    docker push ${DOCKERHUB_USER}/${BASENAME}:${VERSION}

.PHONY: docker-build docker-push
```

One’ll have to run `docker-push` via `echo $MY_TOKEN | make docker-push` which is a little bizzaro. But a human shouldn’t be running this command at all, rather the system should do it.

With this set, I could then operate some process changes, inspired by gitflow:
* I added a new `develop` branch and made this the primary branch in GitHub. Every work will start off of it as a feature / bugfix branch, and end up in it via a merge.
* I relegated the `master` branch to a “log of releases”. It has about 30 commits of history. But from now on it should just be built out of releases of the form “Releases vX.Y.Z”, each with a tag `vx.y.z`.
* Added a `docs/releases/version-x.y.z.md` series of documents, which are the release notes log too!
* Other than this, it’s a standard gitflow process. There’s no other scripts, though they will come.

Finally the `release.yml` file can be morphed by restricting it only to the `master` branch with certain tags, and using the new `docker-push` rule:

```yaml
name: Release

on:
  push:
    branches:
     - master
    tags:
     - v*

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
     - uses: actions/checkout@v2
     - name: Build the docker image
       run: make docker-build
     - name: Publish the docker image
       run: echo $(( secrets.DOCKERHUB_TOKEN )) | make docker-push
```

OK, this should be about it. Took a bit of time, but hopefully the gradual buildup of something more professional-looking can help you in your projects. There’s still a bunch to go for the future:
* Having some `git flow` style scripts in the repo.
* Learning to squash commits on the `master` branch.
* Building a `scripts` directory both the make and Actions can reference.
* Factoring out the steps into actions referencing the scripts.
* Adding some tests (!) and having tests run as a separate workflow for each branch.
But those I’ll add in later efforts. Till next time.
