---
layout: post
title: "Announcing Jupiter"
date: 2020-02-22 07:20:05
categories: post
tags: jupiter
comments: true
---
Today I’m releasing a small open source project. It’s been a while since I did so. I’m excited though because it’s something I built for myself and which I’m using heavily in my day to day life. It’s not just some academic exercise or some feel-good effort after a larger abandoned project. I am doubly excited because the project itself is quite rough, and unfinished, and stupid in many places. Fighting that perfectionism bug one crappy release at a time.

The project is named [jupiter](https://github.com/horia141/jupiter) and it’s a small application for goals management, task tracking, habit building, and all that jazz. More precisely it adds a bunch of magic to [Notion.so](https://notion.so) - an already existing and quite good productivity app which is a sort of cross between Trello, Jira, and Confluence. The “magic” is just a bunch of conventions on how work is organized. There is a growing set of CLI scripts for maintaining these conventions and automating such things like recurring task creation, task archival, etc. But yeah, you read that right, it’s an CLI app right now. It’s a surprisingly convenient form given that most of the interaction happens via Notion. Realistically I would not have had the bandwidth for anything else - be it webapp, native app, desktop app, Electron, or any other form modern consumer facing apps take.

![Jupiter Demo](/assets/jupiter-demo.gif)

You can checkout the code itself on GitHub. There’s a short tutorial there too. But I’ll cover some of that material here as well. The rest of the post is divided in two. I’ll speak a bit about how the project came about, and then I’ll deep dive into the tutorial.

# Origin

Jupiter had a convoluted birth. About a year ago I decided my current system(s) for keeping track of “life” weren’t cutting it. I was especially frustrated that there were many of them - Trello for recurring tasks, docs for ToDos and reading lists, spreadsheets for plans and researches, Google Keep for some other lists, Google Calendar for tasks with deadlines, and gmail(s) for yet other sorts of tasks, etc. It was hard to manage and I was not keeping up! So I set out to document what I’d need from a single tool, and try to buy or build a solution. The scope increased - to something to keep track of all of life, plan major life goals, establish habits, drive complex projects, and also help with paying the bills and doing the various chores of life. Of course no tool could satisfy the reqs, therefore I decided to build one. I did try to massively de risk the project and build it as a CLI app, with technology I knew well, simple design, etc.

In the end I built a bunch of stuff, some of it useful, but never enough to handle everything. And I never migrated to it. And there was never enough time to hack on it anyways.

There I was in limbo till I found Notion. It is an awesome and magical product. And massively more polished than anything I could build - it had multi platform apps, was fast, and had a good conceptual core for what I ai wanted to achieve. The support for collections with multiple views, including an elegant Kanban, calendar and plain ol database was golden. I could see myself using it. The only downside was there was no support for recurring tasks. I could not see the bank being understanding of missed payments because I forgot to do some bookkeeping here.

But there was an API. An unofficial one, but it existed and worked, After some hesitation I started building a small script to take some YAML definitions and sync them to a specially prepared Notion.so collection. It was interesting to pull off, and the singles hardest part of the whole project. But at the end ai had a script which could reliably and idempotently synchronize the local git repo with Notion. I immediately started using the system and began migrating everything to it ASAP. A bunch of big improvements later, there’s still something quite raw about it. But it was sufficiently nice that I could start publicly sharing it, etc.

# Tutorial

In this last part, I'll provide a quick tutorial. You can find more info in the docs too.

To startup, you'll need a Notion account. It's free to setup, but you'll eventually need to sign up for the paid version if you want to use it properly. The first four months are free however, regardless, so you'll get a good feel for wether it's useful for you or not.

Once that's done, you'll need two crucial pieces of information - your space id, and a token for accessing the API. These can be gotten via …

Once that's out of the way, we can begin the script setup proper.

Right now, the simplest and only way org getting this is via sources. You can fit clone and pip install stuff.

Then create a repo. Fill in stuff.

Then do an initial and what it does.

Then create some extent tasks. And create them

Then upset the tasks.

Then do them for another day.

And other tasks too.

And then you can have big plans too.

Finally commit and write.
