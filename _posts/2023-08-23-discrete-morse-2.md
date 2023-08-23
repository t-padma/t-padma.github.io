---
layout: article
title: Discrete Morse Theory - II
mathjax: true
tags: morse_theory intro alg_topo
---

The current post is a continuation of an earlier post [Discrete Morse Theory - I](https://t-padma.github.io/2023/07/30/discrete-morse.html). While part one focused mostly on topological concepts, the second part will focus on combinatorial interpretations and constructions associated with a simplicial complex. The primary reference is Chapter 10 of the textbook "**Organized Collapse: An Introduction to Discrete Morse Theory**" by Dmitry N. Kozlov[^2]. $\mathcal{K}$ denotes an abstract simplicial complex unless specified otherwise.

### Simplicial complexes and Posets
A simplicial complex $\mathcal{K}$ can be made into a poset by defining a partial order $\geq$ on the set $\mathcal{K}$ of simplices. 

$$
\sigma \geq \tau \text{ iff } \sigma \supseteq \tau
$$

Such a poset $(\mathcal{K}, \geq)$ is called the **face poset of** $\mathcal{K}$ and it is denoted by $F(\mathcal{K})$.

Conversely, given a poset $P$, we can construct a simplicial complex $\triangle(P)$ using the fact that chains in a poset are totally ordered subsets. Hence $\triangle(P)$ is called the **order complex** of $P$. 
* $\triangle(P)^0$ = vertices of $\triangle(P)$






















[^1]: Bauer, U., and Edelsbrunner, H. (2016), "[The Morse theory of Čech and Delaunay complexes](https://doi.org/10.1090/tran/6991)", Transactions of the American Mathematical Society, American Mathematical Society (AMS).
[^2]: Dmitry N. Kozlov (2020), "[Organized Collapse: An Introduction to Discrete Morse Theory](https://www.maa.org/press/maa-reviews/organized-collapse-an-introduction-to-discrete-morse-theory)", Graduate Studies in Mathematics, American Mathematical Society (AMS).
