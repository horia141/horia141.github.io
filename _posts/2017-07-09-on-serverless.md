---
published: true
title: On Serverless
layout: post
date: 2017-07-09 15:15
categories: post
tags: distributed_systems internet_applications serverless
comments: true
math: false
---

If we ever were to rank technology trends by choice of bad name, then serverless would easily make it to the top. Which is unfortunate, as I think that despite the name, serverless is a very important development and possibly the last step towards a very interesting cloud vision.

Serverless is an approach for the _compute_ component in a cloud computing platform, where application code is run in a stateless container which is fully managed by the platform. The name comes from the fact that there is _no server to manage_, rather than there not being a server at all. (Servers to manage)-less does not have the same ring to it, though, so serverless has stuck.

What do we mean when we say that there is no server to manage though? First of all, operationally, there is no concept of provisioning a machine/VM/container, specifying an OS for it, configuring it and managing its lifecycle via something like Chef or Puppet, monitoring it, deploying code to it, worrying about it going down etc. Basically, most of the stuff an Ops team would do, doesn’t need to be done anymore. Second, billing is done in terms of requests served, memory consumed, data consumed etc. rather than machine hours.

From both points of view serverless is a natural and I would argue, good evolution towards Compute As A Service. But to fully explain what I mean, we need some context.

The server-side part of an internet application is composed of several services. Some of them are off-the-shelf components, such as databases, distributed queues, lock services or logging systems, while others are custom built, such as application logic servers. While cloud providers started by offering generic VMs to run every component by hand and under the control of the user, they quickly added managed offerings for the off-the-shelf components. The selling points were not eliminating the need to take care of the service and billing at the granularity of whatever resource unit was important for that service. The same story as for serverless basically. And not at all a coincidence.

However, for the longest time, the custom components of application were excluded from this process. You would use a powerful and fully managed solution such as [DynamoDB](https://aws.amazon.com/dynamodb/) or [Cloud Datastore](https://cloud.google.com/datastore/), but then have to worry about capacity planning for your application servers, server lifecycle management, OS patching, monitoring etc. There were some early attempts at Compute As A Service, such as Google App Engine, but a number of issues doomed them. Mostly being too ahead of the curve on one hand, and not enough investment from the provider on the other hand.

Yet, since 2014 and Amazon’s launch of [AWS Lambda](https://aws.amazon.com/lambda/), things have picked up momentum. Azure now has [Azure Functions](https://azure.microsoft.com/en-us/services/functions/) and Google has [Cloud Functions](https://cloud.google.com/functions/). And we can speak of serverless as a _thing_, worry about what it means for the future of the cloud and write snarky tweets about there still being servers, goddamit. So what has changed?

One reason is that so many other components have been made into services successfully, it made people interested in having the last bastion of application logic as a service as well. If a user is comfortable with all their data being in a third party managed service, they should be comfortable with the code being as well. And since so many of the other offerings have delivered, it bodes well for the compute products as well. The major difference is that compute focuses on code, while all the other services focus on data. But the principle is the same.

Another reason is that horizontal scaling of a service, stateless services, microservice / SoAs and [The 12 Factor App](https://12factor.net/) have won as architectural choices for medium to large-scale internet applications. In this context, having a compute service which offers highly scalable execution of a stateless function doesn’t seem like such a bad offering, since that was what you’d build by hand anyway. That wasn’t the way most people were used to do things way back in 2008 when App Engine was built, for example.

Slowly it seems, most cloud providers are building [PaaSes](https://en.wikipedia.org/wiki/Platform_as_a_service) as well to go alongside their [IaaS](https://azure.microsoft.com/en-us/overview/what-is-iaas/) offerings. Which is a good thing. Because it means you can built a quick prototype with the PaaS parts of a cloud platform, and as things evolve you can slowly move to the IaaS parts, but still stay on the same platform. From the other direction, providers of highly specialized services such as [BaaS/mBaaSes](https://en.wikipedia.org/wiki/Mobile_backend_as_a_service) are beginning to offer facilities to run application logic on behalf of clients, as the functionality starts to become expected. This effectively turns them into providers of serverless infrastructure.

As a developer it’s worthwhile to keep an eye out on the developments in the serverless space. Wide adoption would have far reaching implications for the way we build applications, as well as for related/competing technologies such as VMs, Docker/lxc & all the infrastructure built or being built around them. My hope is that this is another point where the barrier to building something in a professional manner gets lowered.

There’s still a lot of uncharted waters and a lot of things for the industry as a whole to learn. There’s also a lot of downsides to serverless, and many of them are detailed in the extra references, which are well worth the read.

Extra references:

- [Serverless computing](https://en.wikipedia.org/wiki/Serverless_computing)
- [What is serverless](https://auth0.com/blog/what-is-serverless/)
- [Serverless Architectures](https://martinfowler.com/articles/serverless.html)
- [Serverless: the next big transition?](https://conferences.oreilly.com/software-architecture/sa-ny/public/content/the-next-big-transition)
- [Serverless architecture in short](https://specify.io/concepts/serverless-baas-faas)
- [A look at serverless architectures](https://dzone.com/articles/serverless-architecture-1)
- [Serverless vs PaaS and Docker: Three-legged shaved Yaks](https://serverless.zone/serverless-vs-paas-and-docker-three-legged-hairless-yaks-f2c4191b1ed6)
- [FaaS, PaaS, and the benefits of serverless architecture](https://www.infoq.com/news/2016/06/faas-serverless-architecture)
- [The 12 Factor App](https://12factor.net/)
- [Why NoOps is a DevOps disaster waiting to happen](https://devops.com/noops-devops-disaster-waiting-happen/)
