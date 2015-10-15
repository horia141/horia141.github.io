---
layout: post
title: "Optimal Predictors"
date: 2015-10-13 21:18:05
categories: post
tags: statistics math machine_learning applied_mathematics
comments: false
math: true
---
This post is about a neat question I was asked many moons ago in an interview. I had never encountered such a problem before, but was quite pleased with myself after being able to figure it out in a high-pressure interview setting. I've changed some bits of the problem statement in order to protect the innocent.

__Problem__ Suppose you are have a car engine and wish to know its operating temperature. Regulation says that you're not supposed to 


[ the problem itself ]
[ talk about the form the combination might take. settle on the convex combination ]
[ figure out what we might try to do - variance minimization ]
[ solve the problem through optimization and Lagrangians ]
[ generalize ]

Say you have two predictions $$X_1$$ and $$X_2$$ and you have standard deviations $$s_1$$ and $$s_2$$ for them. Then, you can build a better predictor as a weighted average of the two, $$Y = w_1 X_1 + w_2 X_2$$, with a variance $$s^2 = w_1^2 s_1^2 + w_2^2 s_2^2$$. $$w_1 + w_2 = 1$$ and $$w_1, w_2 > 0$$ (they are a convex combination). The goal is to choose them in a principled way, rather than just “guessing”.

One approach is to try to minimize the standard deviation / variance $$s^2$$. If we pose the optimization problem as given above and apply the proper conditions, then, by Lagrange multipliers optimization we’ll be able to obtain the following values for the weights: $$w_1 = s_2^2 / (s_1^2 + s_2^2)$$ and $$w_2 = s_1^2 / (s_1^2 + s_2^2)$$, which satisfy all our constraints.

Notice the interesting ways in which the standard deviations influence the weights. If a sd is small, the weight of the other predictor will be small.

This can be generalized to $$k$$ predictors, where we get $$Y = \sum_{i=1}^k w_i X_i$$ and $$s^2 = \sum_{i=1}^k w_i^2 s_i^2$$. We get $$w_i = \prod_{j=1}^k s_j^2 / s_i^2 \sum_{j=1}^k s_j^2$$. The same kind of influence occurs. If a predictor $$X_i$$ has small variance, then the weights of all the other predictors are reduced. [ Check if this is alright ]

If the variances are equal, we end up with a simple arithmetic mean of the predictors.