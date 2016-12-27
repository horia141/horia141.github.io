---
published: false
layout: post
date: 2016-09-21 10:12:23
categories: post
tags: python docker web_dev
comments: false
---
Docker has ceased to be the _new hotness_ in developer circles and has gained a place in the toolkit of many developers. At least when it comes to non-production use cases, for the moment.

Given its popularity, and, _perhaps_, central place in the infrastructure layer of many systems, it is still surprisingly hard to _grok_ Docker.

By that, I mean, use it in a way in which it gives you the benefits, but does not impede your ability to build stuff.

In this post I'll talk about a receipe for building decent Dockerfiles.

First, what are some advantages of Docker in development:
 * Isolation between the host machine and the built system.
 * An explicit specification of what it is that a particular component needs for it to function.

In development it is very important to keep iteration cycles low. The time between making a change and being able to test it should be imperceptible. The further away one is from this ideal, the greater chances of [this](https://xkcd.com/303/) happening.

However, when writing Docker files, it is very easy to build things which take a very long time to rebuild.

Describe Python package and how the app is written as such.

Here's how the thing should look like, after me, as a template.

The first bit should be the very highest-level properties of the image. I've been using the `ubuntu:latest` image, but you're free to use whatever.

{% highlight dockerfile %}

FROM ubuntu:latest
MAINTAINER Horia Coman <horia141@gmail.com>

{% endhighlight %}

Next comes installing the distribution provided packages. These are things like programming language runtimes, compiler utilities, large packages. The general purpose stuff you're likely to find in your distribution. Since we're using `ububtu` we'll be using `apt` for this. Notice tha particular invocation. Everything is installed in one command. `apt-get update` is called beforehand to make sure the `apt` cache is up to date. Finally `apt clean` is called to remove temporary files. This is because everyfile produced is going to result in a larger final image. As with everything computers, the smaller the better. Everything is run as one command so in case there is a change, fresh versions of the package will be refetched.

I try to keep things to a minimum here. One way to do that is to keep components small and focused, by employing a microservices approach to things. Another way is to install programming language specific bits from the particular package repository, even if the same package is available in `apt`.

There's a dark art in figuring out exactly what you need from the platform package manager. One would think that `python3` is enough. Unfortunately many Python packages need to build some code as part of their installation process. For this they need the other packages specified here, even though they are not explicitly declared. It's an iterative process at first.

You might be thinking that, if this list gets too big, you will again have very large build times, because adding/removing packages will result in a storm of changes. This is certaintly true, but in my experience, such changes are rare. If you find yourself constantly making changes, perhaps there's a deeper problem. Or perhaps you truly need to explore alternatives.

{% highlight dockerfile %}

RUN apt-get update -y && \
    apt-get install -y --no-install-recommends \
            libffi-dev \
	        libpq-dev \
            libssl-dev \
            python3 \
            python3-dev \
            python3-pip \
            python3-setuptools \
            build-essential && \
    apt-get clean
    
{% endhightlight %}

The next step is a little bit project specific. It creates some directory structure for the thing. I like to have all the things under the control of the program in a single directory. Makes debugging easier. No reason to respect Unix traditions etc. inside the container. Everything will live under `service`. There's a `pack` directory where the package contents are copied to and a `var` directory where things like logs, SQLite databases, locks etc. live. This is under your control in the end though.
Also `service` is a placeholder. Feel free to use whatever you deem appropriate for your application.

{% highlight dockerfile %}

RUN mkdir /service
RUN mkdir /service/pack
RUN mkdir /service/var

{% endhighlight %}

The next step is creating a user and group for the application. It is good practice, even in Docker, not to run things as root. This will help if ever you need to run the thing outside of Docker, as well. See more info [here](link).
Again `service` is a placeholder. No reason not to make it the same as the work directory name though.

{% highlight dockerfile %}

RUN groupadd service && \
    useradd -ms /bin/bash -g service service
    
{% endhighlight %}

Next comes a tricky bit. We copy the `requirements.txt` file at the root of the package, and then install all its dependencies. Using the requirements file actually saves our bacon here, because it can be copied as is, without any of the other code, and we'll have everything we need to be good to go, from sources.

{% highlight dockerfile %}

COPY requirements.txt /service/pack/requirements.txt
RUN cd /service/pack && pip3 install -r requirements.txt

{% endhighlight %}

# Copy source code.

COPY . /ocelot/pack

# Setup the runtime environment for the application.

ENV ENV LOCAL
ENV ADDRESS 0.0.0.0
ENV PORT 10000
ENV MIGRATIONS_PATH /ocelot/pack/inventory/migrations
ENV IDENTITY_SERVICE_DOMAIN ocelot-identity:10000
ENV DATABASE_URL postgresql://ocelot:ocelot@ocelot-postgres:5432/ocelot
ENV CLIENTS localhost:10000
ENV PYTHONPATH /ocelot/pack/inventory/src

RUN chown -R ocelot:ocelot /ocelot
VOLUME ["/ocelot/pack/inventory/src"]
WORKDIR /ocelot/pack/inventory/src
EXPOSE 10000
USER ocelot
ENTRYPOINT ["gunicorn", "--config", "inventory/config.py", "inventory.server:app"]

{% endhighlight %}


The rule to follow is - the more likely something is to change, the later on in the Dockerfile one should put it. Even though it doesn't look as pretty, and is not as organized as one might like. Ideally, the Dockerfile itself should not be that large.

One downside of this is that the resulting images are quite big. Since I haven't been using Docker in production, and this is mostly for exploration and side-project use, I haven't spent time optimizing this aspect.

