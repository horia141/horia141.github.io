---
published: true
layout: post
date: '2018-09-07 07:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #52'
---
Celebrating one year of posting these things! Or the 52nd post to be more precise, which is a bit over a year, on account of some major laziness.

[How Dropbox securely stores your passwords (2016)](https://blogs.dropbox.com/tech/2016/09/how-dropbox-securely-stores-your-passwords/) - a more up-to-date approach for password storing than simply "hash with `bcrypt`". The first step is a `SHA512` on the client side, to get the password to a "normal state". Then the regular `bcrypt` password function as the workhorse of protection. Finally, `AES256` encryption with a well known (but still secret) key. The latter is simply a defence in depth approach.

[Password and credential management in 2018 (2018)](https://medium.com/@harwoeck/password-and-credential-management-in-2018-56f43669d588) - an extension of the previous post, with even nicer goodies. Not written by a big company, but the ideas are still good. The first `SHA512` step is extended to include a global salt, to make even the data sent from client to server unique to the service and mitigate some parts of password reuse. `bcrypt` is optionally replaced with `Argon2d`, a newer/better/not yet as tested KDF. Finally the last encryption step is replaced with `ChaCha20-Poly1305`, an alternative and newer symmetric encryption algorithm. There is also a nice discussion on storing API keys and other such secrets. Again, from the perspective of the service providing them. These are, again "passwords", and even if no human is compromised because they're revealed, it's still super important to get security for them right.

[The RED Method - how to instrument your services (2018)](https://grafana.com/blog/2018/08/02/the-red-method-how-to-instrument-your-services/) - nice service-centric approaches to looking at a service's metrics - look at request volume, error volume and request latency as a baseline for how you understand a service. This should be coupled with machine metrics (CPU, memory, IOs of various sorts), dependent infra metrics (DB reads/writes and problems with them, cache hits etc) and higher level business metrics for the service (how many "clients" currently active, various business-level errors etc).

[Using Python's type annotations (2018)](https://blog.danstarner.com/python-type-annotations/) - I've been a bit away from Python land lately. I was aware type annotations were a thing, but that was about it. This proved to be a nice introduction. Hopefully a type checker / linter is around the corner.

[Stop future proofing software (2018)](https://medium.com/@george3d6/stop-future-proofing-software-c984cbd65e78) - wise words here. Basically, the advice is to build something fast and release it to clients as is, and worry about scaling when there's actual scale. Fairly pointed to "Internet applications", but still good stuff. There's also a nice discussion on just how powerful modern machines are, and how many of the advice around designing software to scale is stuck 10 years ago. There's basically a lot vertical scaling can do for you, before you need horizontal one. My experience at StackOverflow and Taxfiy makes me resonate with this advice a lot.
