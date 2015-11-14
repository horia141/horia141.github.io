---
layout: post
title: "Optimal Predictors"
date: 2015-11-14 21:18:05
categories: post
tags: statistics math machine_learning applied_mathematics
comments: false
math: true
---
This post is about a neat question I was asked many moons ago in an interview. I was quite pleased with myself for getting it right, especially [under pressure](https://www.youtube.com/watch?v=a01QQZyl-_I). I've changed some bits of the problem statement in order to protect the innocent, however.

__Problem__ Suppose we have a car engine and wish to know its current temperature $$t$$. We could use a temperature sensor to obtain measurements of the temperature. However, these readings aren't precise. One minute we might get a value, the next minute a slightly different value. For this reasons, regulation says that we're supposed to use at least two temperature sensors, from two different vendors, in order to get a more reliable reading. The rules are fuzzy however about how to go about combining sensors. We want to do a good job however and seek to find the best possible way to combine measurements.

For argument's sake, I'm going to focus on the simplest case, that of two sensors.

A first hurdle is correctly describing the problem in the language of mathematics. We can model the measurement obtained from the first sensor by a random variable $$T_1$$ and the one from the second sensor by a random variable $$T_2$$. I'm also going to make the assumption that the sensors are good, and actually measure the temperature, without any bias, such that $$\mathbb{E}[T_1] = t$$ and $$\mathbb{E}[T_2] = t$$. Finally, I'm going to assume that the random variables are fully characterized by their variance $$\mathbb{V}[T_1] = s_1^2$$ and $$\mathbb{E}[T_2] = s_2^2$$, which is a measure of the quality of the sensor. This variance is known, and in real life it would be provided by the manufacturer.

We can formulate the problem in a nicer fashion now. Our goal is to find $$f^\star$$ with $$T = f^\star(T_1,T_2)$$ such that a given quality metric $$Q[T]$$ is maximized. Since we've declared that a given sensor is of higher quality if its variance is low, we can use the variance of the resulting estimator as the quality metric, thus $$Q[T] = -\mathbb{V}[T] = -\mathbb{V}[f(T_1,T_2)]$$. The problem then becomes:

$$
f^\star = \arg\min_{f} \mathbb{V}[f(T_1, T_2)]
$$

We've made tremendous progress on modeling the problem. However, the form of $$f$$ is still very fuzzy. How should it look? We could use $$f_1(T_1,T_2) = T_1$$ or $$f_2(T_1,T_2) = T_2$$, that is, defaulting to either one or the other sensor, or even $$f_{max}(T_1,T_2) = X_{\max(s_1^2,s_2^2)}$$, but that feels like a cop-out and is basically against regulation.

In principle, $$f$$ can look like anything. You'll agree with me, however, that an "arbitrary" functions such as $$f(T_1,T_2) = T_1^{\cos{T_2}}$$ looks kind of funky. The most natural approach is perhaps to average the two measurements, like $$f(T_1,T_2) = T_1 + T_2$$. This is a step in the right direction, however, is does not take the different qualities of the sensors into account. A better approach would be $$f(T_1,T_2) = \alpha_1 T_1 + \alpha_2 T_2$$ - a linear combination of the two. The goal could then be modified such that we choose $$\alpha_1$$ and $$\alpha_2$$ in order to minimize the variance. There is a slight problem however. The alphas can be negative or very big etc. Again, it seems unnatural to subtract a measurement. We should restrict the coefficients to be positive. Better yet, we should force them to be a convex combination, such that their sum is always $$1$$. Thus the final measurement is a little bit of the measurement of sensor $$1$$ and a little bit of the measurement of sensor $$2$$. The problem then becomes:

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

In the first line we used a property of the variance, namely that, $$\mathbb{V}[aX] = a^2\mathbb{V}[X]$$, as well as the "almost"-linearity of the variance of independent random variables. The problem is an equality constrained convex optimization problem. A standard tool for solving such problems is that of [Lagrange multipliers][Lagrange multipliers]. The optimization problem can be posed as:

$$
\alpha_1^\star, \alpha_2^\star = \arg\min_{\alpha_1, \alpha_2} \alpha_1^2 s_1^2 + \alpha_2^2 s_2^2 + \lambda (1 - \alpha_1 - \alpha_2)
$$

This form can be attacked through regular tools for unconstrained convex optimization problems. The minimum will be the point for which the gradients along $$\alpha_1$$, $$\alpha_2$$ and $$\lambda$$ are zero. If we look at $$\alpha_1$$, we have:

$$
\begin{equation}
\begin{split}
\frac{\delta}{\delta {\alpha_1}} ( \alpha_1^2 s_1^2 + \alpha_2^2 s_2^2 + \lambda (1 - \alpha_1 - \alpha_2) ) & = 0 \\
\frac{\delta}{\delta {\alpha_1}} \alpha_1^2 s_1^2 + \frac{\delta}{\delta {\alpha_1}} \alpha_2^2 s_2^2 + \frac{\delta}{\delta {\alpha_1}} \lambda (1 - \alpha_1 - \alpha_2) & = 0 \\
s_1^2 2 \alpha_1 - \lambda & = 0 \\
\lambda & = 2 s_1^2 \alpha_1 \\
\end{split}
\end{equation}
$$

Applying the same procedure for $$\alpha_2$$, we obtain $$2 s_2^2 \alpha_2 - \lambda = 0$$. Replacing $$\lambda$$ with the previous expression yields:

$$
\begin{equation}
\begin{split}
2 s_2^2 \alpha_2 - \lambda & = 0 \\
2 s_2^2 \alpha_2 - 2 s_1^2 \alpha_1 & = 0 \\
s_2^2 \alpha_2 - s_1^2 (1 - \alpha_2) & = 0 (~\text{because } \alpha_1 + \alpha_2 = 1) \\
s_2^2 \alpha_2 - s_1^2 + s_1^2 \alpha_2 & = 0 \\
\alpha_2 (s_1^2 + s_2^2) & = s_1^2 \\
\alpha_2 & = \frac{s_1^2}{s_1^2 + s_2^2} \\
\end{split}
\end{equation}
$$

We thus have the form for $$\alpha_2$$ in terms of quantities we know ($$s_1$$ and $$s_2$$). Since $$\alpha_1$$ and $$\alpha_2$$ must add up to $$1$$, we have the final form for them: 

$$
\begin{equation}
\begin{split}
\alpha_1 & = \frac{s_2^2}{s_1^2 + s_2^2} \\
\alpha_2 & = \frac{s_1^2}{s_1^2 + s_2^2} \\
\end{split}
\end{equation}
$$

This is definitely a very nice and satisfying result. For non-negative $$s_1$$ and $$s_2$$, the $$\alpha$$s are unitary values. Since the $$s$$s are standard deviations, we can naturally expect them to meet this criteria. It's also interesting how the dependence works. If the variance for one sensor is large relative to the one for the other sensor, then one coefficient will be small while the coefficient of the other sensor will be large. There are some edge-cases which are worth mentioning. If $$s_1 = s_2$$, we have $$\alpha_1 = \alpha_2 = 1/2$$, which is something we expected. If $$s_1 = 0$$, we have $$\alpha_2 = 0$$, that is, if one sensor provides perfect information, we don't bother with the other sensor. As a side-note, the model breaks down when both sensors are perfect, though it at least indicates that the coefficients should be the same.

We've started with a practical problem, and through a series of modeling decisions and assumptions we've come up with a very nice way to combine the sensors, complete with analytical forms for its parameters. While this is a toy problem, it's still an interesting application of statistical modeling and convex optimization. It can also be naturally extended to the case of $$k > 1$$ sensors, but that's a problem for another time.

[Lagrange multipliers]: https://en.wikipedia.org/wiki/Lagrange_multiplier