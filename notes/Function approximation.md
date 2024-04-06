---
layout: page
permalink: notes/function-approximation
tags: en
title: Function approximation
---

We have **enormous state functions**, having a generic approssimation could really help!
We want to use a *differentiable* value function so that we can use gradient descent to optimize it, for example a good way of loss would be

$$
J(w) = \mathbb{E}_\pi[(V^\pi(s) - \hat{V}^\pi(s;w))^2]
$$

The second one is parametrized with $$w$$. 
There are two ways (recuperali!) MC policy or Time differential (that is boostrapped, instead the Monte carlo uses a full simulation in order to know what to use).
2

# References