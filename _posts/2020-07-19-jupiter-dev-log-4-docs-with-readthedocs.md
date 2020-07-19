---
layout: post
title: "Jupiter Dev Log 4 - Using ReadTheDocs For Docs Hosting"
date: 2020-07-19 07:20:05
categories: post
tags: jupiter
comments: true
series: "Jupiter Dev Log"
---
![Docs](assets/jupiter-docs.jpg)

<span>Photo credit <a href="https://unsplash.com/@jimo?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content
=creditCopyText">James Barnett</a> on <a href="https://unsplash.com/s/photos/script?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">Unsplash</a></span>

Many many months since the [last dev log](https://dev.to/horia141/jupiter-dev-log-3-lint-all-the-things-51lh) have passed. I’ve worked on and off a lot on this thing though, and there’s massive changes still to be released. So no version to actually point to for the code examples in this blog post, even if `develop` is way ahead of `master`. Still, I want to cover _something_, so I figured I can speak about the [public documentation](https://jupiter-goals.readthedocs.io/) and how it’s written, managed, and generated.

Here’s a picture of how it currently looks like:

![Docs home](assets/jupiter-docs-home.jpg)

Every project should have some form of documentation. The baseline is a `README.md` file in the root repo folder giving some hints of usage. This is sufficient at the start, but as the project becomes more complex it starts to show its limitations. Some table stakes features to have for a _next-level_ system are: multi-page/site support, versioned docs linked to releases, Markdown (or equivalent) support, search capabilities, and web integrations (with web search, various microformate, etc).

That’s quite a feature list to support, but luckily the OSS friendly [Read the Docs](https://readthedocs.org/) project exists which perfectly fits the bill. This is basically a docs-as-a-service product. You link it with `GitHub` and the particular repository you wish to host documentation for. Then you organise your docs in a particular way, configure it appropriately, and you get the kinds of docs [jupiter](https://jupiter-goals.readthedocs.io/) now has.

Linking and configuring the sync is a manual process and is done by squishy humans. Everything else however is automated. The main interaction is responding to a webhook triggered by a code push, and building and publishing the docs. So quite similar to a CI/CD system. There was a bunch of config needed to make this happen, and a bunch of their concepts to get familiar with, but nothing too challenging.

My main and really only gripe with Read The Docs is this integration pattern. It's quite old school: login with GitHub, everything gets setup in the background, a webhook is installed on the repo. The config is done on their website, by clicking buttons and typing into text fields. I would have much rather there was some (workable) URL to hit from CI/CD or even a GitHub action to use directly. And everything would be configured from a repo-level file. So all the things that happen as a result of a push were described and code and stored centrally in the repo. It's a small nuisance in the grand scheme of things, but it does feel a little `2010s`.

On to the coding parts now! There is a [`.readthedocs.yaml`](https://github.com/horia141/jupiter/blob/develop/.readthedocs.yml) file in the root of the repository which looks like this:

```markdown
---
version: 2

mkdocs:
  configuration: mkdocs.yml
  fail_on_warning: true

formats: all

python:
  version: 3.7
```

It essentially tells Read the Docs to use [mkdocs](https://www.mkdocs.org/) as the documentation site generator. There is also the [sphinx](https://www.sphinx-doc.org/en/master/) option, and that’s generally the _blessed_ option, but MkDocs is simpler and a better fit for what Jupiter needs in my opinion. There’s also a Python version requirement. This has nothing to do with the `3.8` used by Jupiter itself, but rather refers to what Read the Docs will use for building and compiling the documentation.

The bulk of the configuration is written in the [`mkdocs.yaml`](https://github.com/horia141/jupiter/blob/develop/mkdocs.yml) file, which obviously targets MkDocs, and it currently looks like this:

```markdown
---
site_name: Jupiter
site_description: "Documentation for Jupiter, the life planning tool"
site_author: "Horia Coman"
copyright: "(c) 2020 Horia Coman"
repo_url: https://github.com/horia141/jupiter
repo_name: GitHub

docs_dir: docs

theme:
    name: mkdocs
    highlightjs: true
    hljs_style: obsidian

nav:
    - Tutorial: 'tutorial.md'
    - Concepts: 'concepts.md'
    - Installation: 'install.md'
    - 'How Tos':
          - Workspaces:
                - 'Initialize A Workspace': 'how-tos/workspaces/init-a-workspace.md'
    - Releases:
          - 'Version 0.3.0': 'releases/version-0.3.0.md'
          - 'Version 0.2.0': 'releases/version-0.2.0.md'
          - 'Version 0.1.6': 'releases/version-0.1.6.md'
          - Older:
                - 'Version 0.1.5': 'releases/version-0.1.5.md'
                - 'Version 0.1.4': 'releases/version-0.1.4.md'
                - 'Version 0.1.3': 'releases/version-0.1.3.md'
                - 'Version 0.1.2': 'releases/version-0.1.2.md'
                - 'Version 0.1.1': 'releases/version-0.1.1.md'
                - 'Version 0.1.0': 'releases/version-0.1.0.md'
                - 'Version 0.0.5': 'releases/version-0.0.5.md'
                - 'Version 0.0.4': 'releases/version-0.0.4.md'
                - 'Version 0.0.3': 'releases/version-0.0.3.md'
                - 'Version 0.0.2': 'releases/version-0.0.2.md'
                - 'Version 0.0.1': 'releases/version-0.0.1.md'
```

There’s the usual meta stuff there, but what’s interesting is the definition of the site structure and navigation. MkDocs can pick it up from the `docs` folder, but through trial and error I’ve found out it’s better to explicitly define it, even if it’s more manual work. It results in a nav bar which looks like this:

![Docs ToC](assets/jupiter-docs-toc.jpg)

For local development there is a `make docs` command, which starts a local dev server at `127.0.0.1:8000` where you can check how the docs will look like once a new release is published. It even has hot swapping, which I always find pretty neat!

That’s about it really. It’s not much, but it actually achieves a lot, so the ROI for this work is great.

A thing to include in future work here is running the whole `docs` tree through a preprocessing step, and replacing some inline values via macros. Things like the project’s public name, or some particular URL, etc. can change, so it’s better to keep them nice and tidy so that the various tools can use them uniformly. But that’s a problem for later.

That’s about it for this time, see you next time.
