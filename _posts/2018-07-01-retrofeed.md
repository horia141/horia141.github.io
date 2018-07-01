---
layout: post
title: "RetroFeed Work Log #1 - Idea & Basic Setup"
date: 2018-07-01 08:20:05
categories: post
tags: raynor rpc retrofeed work-log
comments: true
---
Last month I begun an experiment in logging my work on Raynor RPC ([log1](https://horia141.com/raynor-rpc-work-log-1.html) and [log2](https://horia141.com/raynor-rpc-work-log-2.html)). While working on a library is fun, it's better when there's a clearer direction. Like the one provided by a _product_. So with this post I'm changing gears a bit, and will start blogging about a small side-project I'd like to work on, in which I'll integrate Raynor RPC. In any case, much like with Raynor RPC, publicly speaking about this thing will at least help with keeping myself committed to the project. Even if the audience is me and Googlebot. At best, perhaps a real thing will emerge, with users and releases and bugs and angry GitHub threads. In any case, perhaps the info here will prove useful to folks, regardless of where this goes.

In the rest of the post I'll cover the idea itself, a quick overview of the _tech stack_ chosen and a description of the initial development steps.

I'll start off with a spoiler - the project is derivative. It's similar to [dependencies.io](https://www.dependencies.io/) or [requires.io](https://requires.io/) - a tool which keeps track of your project's dependencies and informs you of the latest changes, security issues etc. It's a project I've been toying with for a while, but just never got around to doing it. I'm keen on having proper RSS feed support for it, and various controls for what to report on. So staying up-to date with changes in dependencies fits well into my workflow. Finally, I'm going to call the thing _RetroFeed_. As noted, this isn't anything new under the sun. So the main justification for building it would just be "this is my rifle, there are many like it ...".

OK, now for some interesting bits. The software stack is going to be Node with TypeScript for the backend, NestJs with Express as a web framework, Raynor with Raynor RPC for NestJs for RPC-ish type stuff. I'll use Postgres as a datastore with Redis for caching. I'll use Knex.js as a data access library. I'll use React & it's ecosystem for the frontend bits. The local environment will be run off Docker, with docker-compose. Deployment will be done on Google's cloud. I'll use the managed SQL and Redis offerings, and run Docker in production. But I won't go the Kubernetes route, and simply run the services on a compute node with `docker run`. Infrastructure as code via terraform, of course. Other services I'll be using are GitHub for code hosting, Travis.Ci for builds, NPM for package hosting, Codecov.io for coverage reports, Cypress.io for end to end testing, Auth0 for easy authentication, and GitHub's API for repository _stuff_. The code's going to be released under the MIT license and I'll try to be as open as possible about the things I'm doing.

In terms of _application architecture_, it's going to be _monoliths all the way_. And all the code in a single repository. Ditto, as far as controversial choices go, I'll try to refrain from going full-SPA[1]. If I ever get to the point where it becomes an issue, I'll be sure to regret it and write the mandatory "How RetroFeed moved away from their old monolith to micro-services/serverless/etc" article.

Anyway, I'll keep things short and stop here. The next post is going to deal with setting things up for a `"hello world"` application. Which is more complicated than you'd think nowadays, so stay tuned.

---
[1] What form this might take, I'm not 100% sure now. But, especially with React, I feel like going the SPA route is not so easy for most projects.
