---
published: true
layout: post
date: '2018-04-27 09:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #36'
---

Last week I wanted to better understand JS modules, so the bulk of the links are related to this topic. It's a fast moving domain, so the articles cover a lot of ground.

[JavaScript Modules (2016)](http://jsmodules.io/) - a primer on the actual module system currently being implemented in browser side JavaScript. The way we'll do things "soon".

[Eloquent JavaScript - Modules (2016)](https://eloquentjavascript.net/10_modules.html) - an overview of some of the older "module formats" and of the new module system and its capabilities. Covers hand-rolled module systems, as well as CommonJS and the new module systems, building & bundling. It looks at larger issues of packages, module design etc.

[JavaScript modules (2018)](https://spring.io/understanding/javascript-modules) - covers AMD, CommonJS and ES6 modules.

[A 10 minute primer to JavaScript modules, module formats, module loaders and module bundlers (2017)](https://www.jvandemo.com/a-10-minute-primer-to-javascript-modules-module-formats-module-loaders-and-module-bundlers/) - covers custom modules (how you'd build them by hand), AMD, CommonJS and ES6 modules. But also things like loaders and bundlers, which are also a big part of the technology needed to use modules properly.

[JavaScript modules - a beginner's guide (2016)](https://medium.freecodecamp.org/javascript-modules-a-beginner-s-guide-783f7d7a5fcc) - a larger article focusing on the rationale for using modules, a lot of custom module patterns, AMD, CommonJS, UMD, ES6 modules. Still waiting for part 2 which deals with bundlers.

[Can I please store images in the database now? (2018)](https://dzone.com/articles/can-i-please-store-images-in-the-database-now) - apparently the oft-repeated anti-pattern isn't such a big issue anymore. Databases are perfectly capable of doing a good job with `BLOB`s. However, whether you want to store them there as part of a larger application is another question. Still, for internal apps, or ones where there is a very tight relationship between the data and image/video/PDF stored as a `BLOB`, it might make perfect sense.
