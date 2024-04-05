---
layout: page
permalink: notes/time-complexity
tags: en
title: Time Complexity
---

## Introduction to Time Complexity
This note will build upon know techniques of algorithms analysis explained in [Notazione Asintotica](/notes/notazione-asintotica).
We will need big-$$O$$ notation and $$o$$ notation.
L'idea è che il problema di decisione è decidibile se limito la lunghezza del teorema.
Simile al [numero di Chaitin]([https://en.wikipedia.org/wiki/Chaitin](https://en.wikipedia.org/wiki/Chaitin)%27s_constant), che non è computabile, ma è approssimabile quanto si vuole. In un certo senso è computabile.
The general idea is to ask how the function $$\varphi$$ that maps the longest $$n$$ proof to the number of steps of computation behaves.
### Robustness of the notion of time complexity

The notion of "computational steps" used to measure the time complexity varies along
- Computational models
- definition of computational steps
- The code of the input and output (not always binary, for example big numbers are not fixed size).


### Influence of the Computational Model
In Complexity Theory **the choice of the formal model** influences the complexity class of the model!
This is different from the argument from computational theory of the [Church Turing Thesis](/notes/la-macchina-di-turing#tesi-di-church-turing), where it asserts that a function is Computable in every computational model. See 7.7 in @sipserIntroductionTheoryComputation2012.

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
NOTE: this is invariant with respect to the chosen coding system (if an algorithm is still in P, then it will remain in P even if you change code scheme).

#### PATH is in P
We can prove that the language
$$\left\{ \langle G, s, t \rangle \mid G \text{ is a graph that has a route from } s \text{ to } t \right\}$$
is in $$P$$ class. (Just use [Grafi#BFS](/notes/grafi#bfs) or [Grafi#DFS](/notes/grafi#dfs)).

NOTE: we have worked assuming that the algorithm worked on the nodes, but usually TM work with bits, the thing is that there is a polynomial algo that converts that nodes into binary format, so it is not much of a big deal.

#### Overview of problems in $$P$$ 
<img src="/images/notes/Time Complexity-20240321132710013.webp" alt="Time Complexity-20240321132710013">

### Exponential Complexity Class
The exponential class $$EXP$$ is defined as:

$$
EXP = \bigcup_{i\geq 1} TIME(2^{n^{i}})
$$

This class is common of the algorithms that use backtracking, for example [CSP problems](/notes/csp-problems). Or just brute-force search all the branches.

### Non-deterministic Complexity Class
Let $$N$$ be a non-deterministic decider then we have that a problem is in this complexity class, called $$NTIME$$ if the running time cost $$f: \mathbb{N} \to \mathbb{N}$$ is bounded by that (longest computational branch).
The difference with [#Polynomial Complexity Class](#polynomial-complexity-class) is that here we consider the length of a single branch, but we explore everything at the same time!

<img src="/images/notes/Time Complexity-20240314134202678.webp" alt="Time Complexity-20240314134202678">

Quindi


$$
NP = \bigcup_{i\geq 1} NTIME(n^{k})
$$

#### Clique problem

This problem is in NP, find all sub-graphs where all nodes are connected (this set of nodes forms a complete graph).

We can prove that the problem is in NP because there is an easy non-deterministic algorithm that computes it.

**NP algorithm**
Just
1. Select a subset of nodes from $$G$$. Do it non deterministically.
2. Verify if this subset is a complete graph. If yes add it to the solution set.

We can prove that this is correct, and it works, but it is a non deterministic algorithm, so it isn't easily simulated by deterministic algorithms, even though we proved in [Estensioni di Turing e altre macchine](/notes/estensioni-di-turing-e-altre-macchine) that from the computability point of view it is the same.

**Verifiable**
Given input the graph, and a subset, we need to
1. For each node in the subset, check if it is linked to each other.
2. Return the previous truth result.
So easy.

#### Verifiability
Definition:
$$A$$ is verifiable if exists a TM $$M$$ such that:

$$
w \in A \iff \exists c : M \text{ accepts } \langle w, c \rangle 
$$

If $$M$$ is polynomial then we say that this is **polynomially verifiable**. We can prove that this notion is equivalent for $$NP$$ complexity classes.

#### Th: Verifiability = NP
From a philosophical point of view, if a problem is in NP, we can just guess a solution, or just do brute force. There is no classical algorithmical solution that solves it, or a constructive proof for it.

$$\leftarrow$$: let's suppose we have a $$M$$ that decides non deterministically that language.
On input $$\langle w, c \rangle$$ we sun $$M(w)$$ and if it accepts, return true if the branch is good. ($$c$$ guides us about what non-deterministic branch to choose).

$$\to$$ : let's assume we have a polynomial verifier, we need to build a TM that decides it non deterministically in polynomial time.
choose non deterministically a certificate $$c$$ the encodes the path of the non-deterministic computation. If this accepts then accept!
TODO: fai meglio questa parte