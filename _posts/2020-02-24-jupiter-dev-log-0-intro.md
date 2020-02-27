---
layout: post
title: "Jupiter Dev Log 0 - Intro"
date: 2020-02-24 07:10:05
categories: post
tags: jupiter
comments: true
---
I plan on blogging a bit about the bigger developments on the Jupiter project. Especially those around CI/CD, integration with various 3rd party systems, productionisation efforts, etc. The infra bits as it were. Not so much the “code itself”, cause that usually is straightforward.

But I do want to spend a bunch of time on the system as it is right now, before going into that.

As mentioned in the [announcement](https://dev.to/horia141/announcing-jupiter-bf3), the system is just a CLI app right now. It's written in Python, using version 3.6, and it is a standard console app. It doesn't use any framework, any fancy library, but it does make use of all the goodies in the standard lib - `argparse`, `logging`, `yaml`, etc. [Pendulum](https://pendulum.eustace.io/) is used for some datetime stuff, cause apparently no language can get working with time right in the standard library and we need to rely on Joda/Noda/Pendulum/moment/etc to get something OK.

The choice of Python merits some discussion. For my hobby projects it would not be my first choice these days. I'm in the TypeScript+Node camp and happy with this. However the best/only SDK for [Notion.so](https://notion.so) is [notion-py](https://github.com/jamalex/notion-py), so realistically the choice was made for me. It was by no means a painful process, and the good parts or Python are still good - nice and clean(er) language, massive standard library, many external packages to choose from, etc. The bad or meh parts are still there though. Virtual envs and the multitude of package systems are prime examples here. Package vs non-package (only  `requirements.txt` projects) are still a pet-peeve of mine. Doesn't help that the issue is basically solved in Node land. I understand things are better in Python3.7+, with type annotations, async/await, etc. But due to the distribution mechanism I've chosen and which will be covered in later sections, it's a no go for now.

Anyway, going back to the project overview, the repo structure is quite barebones now. It just looks like this:

```bash
.
├── Dockerfile
├── LICENSE
├── Makefile
├── README.md
├── docs
├── requirements.txt
└── src
    ├── archive_done_tasks.py
    ├── command.py
    ├── create_project.py
    ├── init.py
    ├── jupiter.py
    ├── lockfile.py
    ├── remove_archived_tasks.py
    ├── schedules.py
    ├── schema.py
    ├── space_utils.py
    ├── upsert_big_plans.py
    └── upsert_tasks.py
```

There are the standard `README`, `LICENSE.txt`, `.gitignore`, etc. There's also a `Makefile` with two simple rules for Docker work.

The `Dockerfile` itself is very barebones. It’s based on [Alpine](https://alpinelinux.org/), a standard base image for “small” containers, and the `python3.6` image more precisely. The packages that are installed are as a result of the package dependencies from `requirements.txt`. Otherwise it just copies `src`s, and sets up a proper entrypoint:

```docker
FROM python:3.6-alpine
MAINTAINER Horia Coman <horia141@gmail.com>

RUN apk --no-cache --update add \
    build-base \
    libffi-dev \
    openssl-dev

WORKDIR /jupiter

COPY requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt

COPY src src

ENV TZ=UTC

ENTRYPOINT ["python", "src/jupiter.py"]
```

Finally, the source code is in `src`. There’s just a couple of things to note about the code here:
* It's a very flat structure and relatively unorganised. Don’t go looking for clean code here!
* A useful pattern is the `Command` one. The `init`, `upsert-tasks`, `archive-done-tasks` are implemented like `Command`s actually, setup in the `jupiter.py` _main_ script. They make use of the various other modules.
* Perhaps the trickiest code is in `upsert_tasks.py` and `schedules.py`. These deal with upserting repeating tasks and all the business domain constraints there (repeat period, skips, vacations, etc.). The other are a big more CRUD-ish.

As for whole project stats, this is what [cloc](http://cloc.sourceforge.net/) reports:

```bash
      21 text files.
      21 unique files.
       5 files ignored.

github.com/AlDanial/cloc v 1.82  T=0.06 s (271.4 files/s, 31662.7 lines/s)
-------------------------------------------------------------------------------
Language                     files          blank        comment           code
-------------------------------------------------------------------------------
Python                          12            264             15           1510
Markdown                         3             51              0            117
Dockerfile                       1              6              0             12
make                             1              2              0              6
-------------------------------------------------------------------------------
SUM:                            17            323             15           1645
-------------------------------------------------------------------------------
```

That’s about it for this first installment. Watch out for later ones, and for later developments of the system!
