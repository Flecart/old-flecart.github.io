---
layout: page
permalink: notes/time-complexity
tags: italian
title: Time Complexity
---

This note will build upon know techniques of algorithms analysis explained in [Notazione Asintotica](/notes/notazione-asintotica).
We will need big-$$O$$ notation and $$o$$ notation.

## The Time Complexity Class
### Definition of the Time Complexity Class

> Languages that are decidable in $$O(t(n))$$ time are part of this class, denoted as $$TIME(t(n))$$.  With $$t : \mathbb{N} \to \mathbb{R}^{+}$$. 

Another way to understand this is that if a algorithms **terminates** in at most $$t(n)$$ steps then it belongs to this class.

### Polynomial Complexity Class

The polynomial class $$P$$ is defined as:

$$
P = \bigcup_{i \geq 1} TIME(n^{i})
$$

This is defined as the class of the **reasonable** efficiency programs.

### Exponential Complexity Class
The exponential class $$EXP$$ is defined as:

$$
EXP = \bigcup_{i\geq 1} TIME(2^{n^{i}})
$$

This class is common of the algorithms that use backtracking, for example [CSP problems](/notes/csp-problems). Or just brute-force search all the branches.

### Non-deterministic Complexity Class
Let $$N$$ be a non-deterministic decider then we have that a problem is in this complexity class, called $$NTIME$$ if the running time cost $$f: \mathbb{N} \to \mathbb{N}$$ is bounded by that.
The difference with [#Polynomial Complexity Class](#polynomial-complexity-class) is that here we consider the length of a single branch, but we explore everything at the same time!

<img src="/images/notes/Time Complexity-20240314134202678.webp" alt="Time Complexity-20240314134202678">

Quindi


$$
NP = \bigcup_{i\geq 1} NTIME(n^{k})
$$


### Influence of the Computational Model
In Complexity Theory **the choice of the formal model** influences the complexity class of the model!
This is different from the argument from computational theory of the [Church Turing Thesis](/notes/la-macchina-di-turing#tesi-di-church-turing), where it asserts that a function is Computable in every computational model. See 7.7 in @sipserIntroductionTheoryComputation2012.