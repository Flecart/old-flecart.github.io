---
layout: page
permalink: notes/algo-from-youtube
tags: italian
title: Algo from Youtube
---

Dai video di Abdul Bari 

Ultima modifica: January 21, 2022 10:24 AM
Primo Abbozzo: January 16, 2022 8:31 AM
Studi Personali: No

# 0 Introduction

## Difference algo-prog

Here we try to list and discuss the main differences between the algorithm and the program.

| algo | prog |
| --- | --- |
| Design | Implementation |
|  Any language |  program language |
| Hardware/soft independent | dependent |
|  Analysis | Testing |
|  Domain knowledge |  Programming |

The algorithm step cares about the design of the program. It’s more of a abstract way of thinking (this is also the cause of the independency from the hardware software and OS), when on the other side the program is the implementation.

I think you got the idea of why (intuition...)

I would summarize this in this way:

Algo → top level thinking

Prog → low level implementation.

### Characteristics of algorithm

1. Input (0 or none)
2. Output (at least 1)
3. Definiteness (the instructions must be precise)
4. Finiteness (we have a finite number of instructions)
5. Effectiveness (he only have the instructions that matter)

### Analysis of the algorithm

1. Time (1 unit per instruction)
2. Space (n of words used, or variables used)

These first two are the most important ones, and most analysed in every contest.

But we also have other types of measurement, but they are not always used.

1. Network bandwidth used
2. CPU registers used
3. Power utilized.

## Asymptotic analisys

There are thre main ways to analyze a function in computer science

$$O, \Omega, \Theta$$.

These can all be defined with limits. (c is bounded by an exist)


$$
f(n)=O(g(n)) \iff\lim_{x\to +\infty}\dfrac{f(x)}{g(x)} \leq c
$$



$$
f(n)=\Omega(g(n)) \iff\lim_{x\to +\infty}\dfrac{f(x)}{g(x)} \geq c
$$



$$
f(n)=\Theta(g(n)) \iff\lim_{x\to +\infty}\dfrac{f(x)}{g(x)} = c
$$


# Heap

## Main operations

### Insertion

### deletion

## Heapify

### priority queue

## heapsort

### [no heap] strassens multiplication alg