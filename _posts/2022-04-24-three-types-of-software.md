---
published: true
layout: post
date: '2022-04-24 07:00'
categories: post
tags: career
comments: true
math: true
title: 'Three Types Of Software'
---
Early in my computing career, I came across a neat classification of software. It split things up into systems, 
applications, and scripts. Like all abstractions, it only gets you so far. But I've found it a useful 
conceptual model as an engineer and a manager. And it has interesting things to say about how software is
built, how it's used, and even who gets to write it.

At the base, there is system software. Think of operating systems, compilers, and databases. These are
common and generic building blocks for all the other software we write. They're also undifferentiated and
by themselves don't do much of anything. They need to be put to use in other projects. Compared to the other types 
of software there aren't many production-grade choices here. We're talking about a few operating systems,
ten-ish popular programming languages, and two dozen major storage engines. There are good economic reasons for this
dearth of choices. Getting these things right is hard. Each one is a major undertaking involving hundreds of
highly trained developers. Some are so large they can be thought of as multi-generational endeavors.
Unix or gcc come to mind. Despite their complexity and difficulty, a minority of all software engineers 
work in this area.

Above that, there is application software. Think of every piece of software with a _name_. Consumer-facing
ones would be Photoshop, Excel, Bolt, or TikTok. But there are also innumerable internal applications workers use
to do their jobs. From machine tool control to help desk ticketing software. This software is designed for a
particular job. It may allow customization or even scripting but within limits. Ticketing software won't
be useful for photo editing. It naturally builds atop system software. But also many other types of
application software. This type of application is shorter-lived than the system one. But there are some
notable outliers like Microsoft Office, Google Search, or Midnight Commander which are used decades after
their first release. The vast majority of "professional" software is application software. So it follows 
that the vast majority of professional developers are application developers. 

Finally, there is scripting. This can be something as simple as gluing a spreadsheet with a mail service 
via Zapier. Or as complex as a data analysis script with Numpy. In truth, the majority of all software is 
this type of scripting. The software is very narrow and adapted to a very specific use case. The lifetime 
is of course much shorter. It builds atop application and system software. The folks who write these
things are programmers too. But they're not necessarily professional software developers. Think of a
back-office worker writing some excel formulas. Oa chemistry PhD building a data analysis script.
While the complexity isn't as high as with a big interactive application, it's still programming.
But it's a very clear means to an end and not a thing in itself. Interestingly, it follows that the
majority of programming is done by these non-professionals.

The thing I like about this framework is that it puts on the same spectrum things like NoCode and
microcode programming. And it shows that they're all tools a developer should have and their disposal.
Many folks have a tendency to write a fully-fledged application when a well-maintainer Zapier or RPA would
do the trick. And be much cheaper to develop and allow much faster iteration. Indeed once the validity of
an approach is clear the script can become an application. Indeed there is an interesting phenomenon of
scripts becoming application software, and of application software becoming system software.

I've also found that this process has a fractal nature, and zooming in you can find these three layers
crop up. 

For example, within companies, you often have a platform team. They focus on adapting system software to
the specific needs of the company. Application programming then happens with a much more constrained and
economical tool selection. On the other extreme, scripting has been rather absent with internal
applications. Historically it was about macros or the occasional custom script for particular applications.
But solutions such as RPA, NoCode, and BI have enabled a much higher degree of automation within a company.
I'm expecting more and more customization to be offloaded to non-professional developers driven by the
tools becoming better and the need for software becoming more acute. In this world, professional developers
will focus on the core systems and the user-facing ones. They'll expose data and events and APIs for these
higher-level tools to consume and automate against.

Anyway, that's it for now. Thanks for having patience till the end. I'm filing this thing under the
"career advice" section of this blog. I'll try to return to more prosaic topics in May.
