---
layout: post
title: "Raynor-Chai"
date: 2017-11-12 20:20:05
categories: post
tags: typescript javascript raynor chai
comments: true
---

This post is about [raynor-chai](https://github.com/horia141/raynor-chai), a nifty extension/helper for [chai](https://chaijs.com), the JavaScript assertions library. It allows one to use the methods of [raynor](https://github.com/horia141/raynor) to check that certain objects behave in the way you like.

Using it looks something like this:

{% highlight typescript %}
import * as chai from 'chai'
import { raynorChai } from 'raynor-chai'

class User {
    @MarshalWith(StringMarshaller)
    name: string;
    @MarshalWith(ArrayOf(IntegerMarshaller))
    scoresByDay: number[];

    totalScore(): number {
        return this.scoresByDay.reduce((a,b) => a + b, 0);
    }
}

chai.use(raynorChai);

const user = new User();
user.name = 'Raynor';
user.scoresByDay = [10, 20, 30];

chai.expect(user).to.be.raynor(new (MarshalFrom(User))()); // Assertion passes

const badUser = new User();
badUser.name = 'Raynor';
badUser.scoresByDay = [10, 20.5, 30];

chai.expect(badUSer).to.not.be.raynor(new (MarshalFrom(User))()); // Assertion passes
{% endhighlight %}

Just like raynor it's supposed to go beyond simple type checking you'd get from typescript and instead focus on deeper properties of objects. It's especially useful to test that objects constructed as part of a larger processes are the way they're supposed to be. So if you're testing your REST API you can use the same entity definitions you're using in your application code to see that the API does what it's supposed to do and outputs the things it's supposed to.

There's just one release right now, but I'll try to evolve it as I use it and as Raynor evolves itself. 
