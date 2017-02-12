---
published: true
title: The Three Ways Of XOR
layout: post
date: 2017-02-12T16:16:05.000Z
categories: post
tags: xor information_theory machine_learning
comments: false
math: true
---
We all the XOR operation. It's the cousin of NOT, AND and OR. Like AND and OR, it is a binary boolean function. Unlike them, most programming languages don't have an explicit "logical operator" for it, but rather show only the bitewise version. Regardless, cryptographers love it and machine learning folks fear it. And for very good reasons. Despite its simplicity, there are quite interesting things to say about it, and this article presents three of them.

To begin with, XOR looks like this, in truth-table form:

| a   | b   | a XOR b |
|:---:|:---:|:-------:|
|  0  |  0  |  0      |
|  0  |  1  |  1      |
|  1  |  0  |  1      |
|  1  |  1  |  0      |

_The first way of XOR_ is that it is true when both arguments are different and false when they are the same. So, to paraphrase the description of logical OR, `a XOR b` is true when either `a` is true or `b` is true, but not both. This is the understanding most common when writing program logic. Sadly XOR doesn't appear as an equivalent to NOT, AND and OR, as a logical operator on booleans, being relegated to just a bitewise operator in most programming languages. This not such a great loss however. XOR doesn't play well with short-circuiting and can lead to bugs in code, if one expects a XOR to guarantee at least a single execution of a block.

_The second way of XOR_ is that it is a controlled NOT. The first argument controls whether the second argument is negated or not. This is the understanding most common in cryptography, where XOR appears as a basic building block of ciphers. The key is used to control the negation, while the plaintext is what is negated. It also appears as a nifty tool in circuit design. Also notice that XOR is symmetrical. The arguments can swap their roles, depending on what we need.

_The third way of XOR_ is that it is the most "complex" binary boolean function. There are $$2^{2^{2}} = 16$$ distinct boolean functions of two operators. Half of them are the negation of another function, so let's list the $$8$$ which are distinct.

| Name | 00  | 01  | 10  | 11  | Entropy | Sep? |
|:-----|:---:|:---:|:---:|:---:|:-------:|:----:|
| zero |  0  |  0  |  0  |  0  | 1.00 | Yes |
| and  |  0  |  0  |  0  |  1  | 1.44 | Yes |
| a!b  |  0  |  0  |  1  |  0  | 1.44 | Yes |
| a    |  0  |  0  |  1  |  1  | 1.50 | Yes |
| !ab  |  0  |  1  |  0  |  0  | 1.44 | Yes |
| b    |  0  |  1  |  0  |  1  | 1.50 | Yes |
| xor  |  0  |  1  |  1  |  0  | 1.50 | _No_ |
| or   |  0  |  1  |  1  |  1  | 1.44 | Yes |

We can see XOR looks slightly odd among the set. While there are other functions with two zeros and two ones, they're all just copies of one of the arguments. From an information theoretic point of view, it has the highest [entropy](https://en.wikipedia.org/wiki/Entropy_(information_theory)) in the set (along side the other functions with $$2$$ ones). Furthermore, from a geometric and machine learning point of view, the function is not [linearly separable](https://en.wikipedia.org/wiki/Linear_separability). It's the only one which is not so from the set. It was in fact [_the_ example](http://www.ece.utep.edu/research/webfuzzy/docs/kk-thesis/kk-thesis-html/node19.html) used against [Perceptrons](https://en.wikipedia.org/wiki/Perceptron) to highlight their limitations. This in turn was one of the seeds for the [AI Winter](https://en.wikipedia.org/wiki/AI_winter) of the late 80s.

As an extra treat, XOR can be considered an imparity function. When its input has an even number of zeros, the output is zero. Otherwise it is one.

Quite the punch for such a small function.
