---
published: true
layout: post
date: '2019-07-19 07:00'
categories: post
tags: friday_blast links
comments: true
math: true
title: 'Friday Blast #75'
---
[TensorFlow.js - machine learning for web and beyond (2019)](https://blog.acolyer.org/2019/02/04/tensorflow-js-machine-learning-for-the-web-and-beyond/) - an overview of the TensorFlow.js paper. It's pretty impressive how this can handle both training and inference in JS via WebGL! It uses "old timey" tricks of expressing non-graphics code in terms of shaders and graphics operations and the performance is quite decent! Seems like the abstraction layers between JS and the GPU aren't that big!

[Sven myths in machine learning research (2019)](https://crazyoscarchang.github.io/2019/02/16/seven-myths-in-machine-learning-research/) - this was quite an interesting read, though it does conflate ML with Neural Networks. What was interesting was the "every datapoint is used in training a neural network" myth and how it relates the approaches of SVMs and NNs with regards to exploration of the input distribution. Namely, both _kinda_ focus on interesting examples, usually near the edge of the decision boundary or surface which is being estimated.

[Supercookies (2019)](https://www.johndcook.com/blog/2019/02/08/supercookies/) - an overview of "other tracking" methods, beside regular cookies. John D Cook has spent some time on this topic, but suffice to say, we're pretty trackable regardless of whether cookies are enabled or not.

[A brief history of AWS architectures (2019)](https://cloudonaut.io/a-brief-history-of-aws-architectures/) - where is your company stuck? In any case, I'm curious how many folks have used the big "container" or "serverless" offerings from AWS at scale. I've had mixed results with some of their offerings which seemed magical - loads of bugs, loads of not-intuitive performance behaviours. It's understandable when folks are loath to switch over from their _known but flawed_ systems to the _unknown and flawed_ ones.

[AWS costs every programmer should know (2019)](https://david-codes.hatanian.com/2019/06/09/aws-costs-every-programmer-should-now.html) - really cool synthesis of the AWS pricing page. Focuses on basic compute (which at it's cheapest is 30$/month for one modern CPU with 4 cores), storage, bandwidth and memory. This about covers it, since many other services are expressed in terms of these basic units!
