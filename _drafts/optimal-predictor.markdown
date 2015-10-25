---
layout: post
title: "Optimal Predictors"
date: 2015-10-13 21:18:05
categories: post
tags: statistics math machine_learning applied_mathematics
comments: false
math: true
---
This post is about a neat question I was asked many moons ago in an interview. I was quite pleased with myself for getting it right, especially [under pressure](https://www.youtube.com/watch?v=a01QQZyl-_I). I've changed some bits of the problem statement in order to protect the innocent, however.

__Problem__ Suppose we have a car engine and wish to know its current temperature $$t$$. We could use a temperature sensor to obtain measurements of the temperature. However, these readings aren't precise. One minute we might get a value, the next minute a slightly different value. For this reasons, regulation says that we're supposed to use at least two temperature sensors, from two different vendors, in order to get a more reliable reading. The rules are fuzzy however about how to go about combining sensors. We want to do a good job however and seek to find the best possible way to combine measurements.

For argument's sake, I'm going to focus on the simplest case, that of two sensors.

A first hurdle is correctly describing the problem in the language of mathematics. We can model the measurement obtained from the first sensor by a random variable $$T_1$$ and the one from the second sensor by a random variable $$T_2$$. I'm also going to make the assumption that the sensors are good, and actually measure the temperature, without any bias, such that $$\mathbb{E}[T_1] = t$$ and $$\mathbb{E}[T_2] = t$$. Finally, I'm going to assume that the random variables are fully characterized by their variance $$\mathbb{V}[T_1] = s_1^2$$ and $$\mathbb{E}[T_2] = s_2^2$$, which is a measure of the quality of the sensor. This variance is known, and in real life it would be provided by the manufacturer.

We can formulate the problem in a nicer fashion now. Our goal is to find $$f^\star$$ with $$T = f^\star(T_1,T_2)$$ such that a given quality metric $$Q[T]$$ is maximized. Since we've delcared that a given sensor is of higher quality if its variance is low, we can use the variance of the resulating estimator as the quality metric, thus $$Q[T] = -\mathbb{V}[T] = -\mathbb{V}[f(T_1,T_2)]$$. The proble then becomes:

$$
f^\star = \arg\min_{f} \mathbb{V}[f(T_1, T_2)]
$$

We've made tremendous progress on modeling the problem. However, the form of $$f$$ is still very fuzzy. How should it look? We could use $$f_1(T_1,T_2) = T_1$$ or $$f_2(T_1,T_2) = T_2$$, that is, defaulting to either one or the other sensor, or even $$f_{max}(T_1,T_2) = X_{\max(s_1^2,s_2^2)}$$, but that feels like a cop-out and is basically against regulation.

In principle, $$f$$ can look like anything. You'll agree with me, however, that $$f(T_1,T_2) = T_1^{\cos{T_2}}$$ looks kind of funky though. The most natural approach is perhaps to average the two measurements, like $$f(T_1,T_2) = T_1 + T_2$$. This is a step in the right direction, however, is does not take the different qualities into account. A better approach would be $$f(T_1,T_2) = \alpha_1 T_1 + \alpha_2 T_2$$ - a linear combination of the two. The goal could then be modified such that we choose $$\alpha_1$$ and $$\alpha_2$$ in order to minimize the variance. There is a slight problem however. The alphas can be negative or very big etc. Again, it seems unnatural to substract a measurement. We should restrict the coefficients to be positive. Better yet, we should force them to be a convex combination, such that their sum is always $$1$$. Thus the final measurement is a little bit of the measurement of sensor $$1$$ and a little bit of the measurement of sensor $$2$$. The problem then becomes:

$$
\begin{equation}
\begin{split}
\alpha_1^\star, \alpha_2^\star & = \arg\min_{\alpha_1, \alpha_2} \mathbb{V}[\alpha_1 T_1 + \alpha_2 T_2] \\
& = \arg\min_{\alpha_1, \alpha_2} \alpha_1^2 \mathbb{V}[T_1] + \alpha_2^2 \mathbb{V}[T_2] \\
& = \arg\min_{\alpha_1, \alpha_2} \alpha_1^2 s_1^2 + \alpha_2^2 s_2^2 \\
\text{st } & \alpha_1 > 0 \\
\text{and } & \alpha_2 > 0 \\
\text{ and } & \alpha_1 + \alpha_2 = 1 \\
\end{split}
\end{equation}
$$

This is an equality constrained convex optimization problem. A standard tool for solving such problems is that of [Lagrange multipliers]...

[ talk about the form the combination might take. settle on the convex combination ]

[ solve the problem through optimization and Lagrangians ]
[ generalize ]

Say you have two predictions $$T_1$$ and $$T_2$$ and you have standard deviations $$s_1$$ and $$s_2$$ for them. Then, you can build a better predictor as a weighted average of the two, $$Y = w_1 T_1 + w_2 T_2$$, with a variance $$s^2 = w_1^2 s_1^2 + w_2^2 s_2^2$$. $$w_1 + w_2 = 1$$ and $$w_1, w_2 > 0$$ (they are a convex combination). The goal is to choose them in a principled way, rather than just “guessing”.

One approach is to try to minimize the standard deviation / variance $$s^2$$. If we pose the optimization problem as given above and apply the proper conditions, then, by Lagrange multipliers optimization we’ll be able to obtain the following values for the weights: $$w_1 = s_2^2 / (s_1^2 + s_2^2)$$ and $$w_2 = s_1^2 / (s_1^2 + s_2^2)$$, which satisfy all our constraints.

Notice the interesting ways in which the standard deviations influence the weights. If a sd is small, the weight of the other predictor will be small.

This can be generalized to $$k$$ predictors, where we get $$Y = \sum_{i=1}^k w_i X_i$$ and $$s^2 = \sum_{i=1}^k w_i^2 s_i^2$$. We get $$w_i = \prod_{j=1}^k s_j^2 / s_i^2 \sum_{j=1}^k s_j^2$$. The same kind of influence occurs. If a predictor $$X_i$$ has small variance, then the weights of all the other predictors are reduced. [ Check if this is alright ]

If the variances are equal, we end up with a simple arithmetic mean of the predictors.