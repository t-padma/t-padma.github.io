---
layout: article
title: Discrete Morse Theory - II
mathjax: true
tags: morse_theory intro alg_topo
---

The current post is a continuation of an earlier post [Discrete Morse Theory - I](https://t-padma.github.io/2023/07/30/discrete-morse.html). While part one focused mostly on topological concepts, the second part focuses on combinatorial interpretations and constructions associated with a simplicial complex. The primary reference is Chapter 10 of the textbook "**Organized Collapse: An Introduction to Discrete Morse Theory**" by Dmitry N. Kozlov[^2]. $\mathcal{K}$ denotes an abstract simplicial complex unless specified otherwise.

### Poset interpretation of Simplicial complexes
A simplicial complex $\mathcal{K}$ can be made into a poset by defining a partial order $\geq$ on the set $\mathcal{K}$ of simplices. 

$$
\sigma \geq \tau \text{ iff } \sigma \supseteq \tau
$$

Such a poset $(\mathcal{K}, \geq)$ is called the **face poset of** $\mathcal{K}$ and it is denoted by $F(\mathcal{K})$.

Conversely, given a poset $P$, we can construct a simplicial complex $\triangle(P)$ using the fact that chains in a poset are totally ordered subsets. Hence $\triangle(P)$ is called the **order complex** of $P$. 
* $\triangle(P)^0$ = vertices of $\triangle(P)$ = elements of $P$.
* $a_m \geq a_{m-1} \geq \cdots \geq a_0$ is a chain in $P$, then $\lbrace a_0, \cdots, a_{m-1}, a_m \rbrace$ is a simplex in $\triangle(P)$

### Matching and simplicial collapse
Matching is the graph theoretic or combinatorial notion for face posets that we use to better understand simplicial collapses. First, we introduce some graph theory definitions where $G = (V, E)$ represents a graph.
* A **partial matching in graph** $G$ is a set of edges $\lbrace \lbrace a_1,b_1 \rbrace, \cdots, \lbrace a_t,b_t \rbrace \rbrace \subset E$ such that all the vertices $\lbrace a_1, \cdots, a_t,b_1,\cdots,b_t \rbrace$ are *distinct*.
* If all the vertices are matched, i.e. $\lbrace \lbrace a_1,b_1 \rbrace, \cdots, \lbrace a_t,b_t \rbrace \rbrace = E$, then such a matching is called a **complete matching**.
* When I say "matching", I am referring to partial matching. Formally, matching is viewed as a function $\mu: M \rightarrow M$ for $M \subset V$ such that:
  - $v$ and $\mu(v)$ are connected by an edge called the **matching edge** for all $v \in M$.
  - $\forall v \in M$, we have $\mu(\mu(v)) = v$. In other words, the vertex $\mu(v) \in M$ is matched to $v \in M$.
* The set M is the set of matched vertices.

Before using a graph theoretic concept to understand face posets, we need a graph representation of a face poset. More generally, we need a graph representation of a given poset $P$. There are different ways to associate a graph to a poset, however, we choose a graph representation called "**underlying graph of the Hasse diagram of P**". Notation used for it is $\mathcal{H}(P) = (V_H, E_H)$ and the graph is defined as follows:
1. $V_H = P$ where $P$ is a poset with a well defined partial order $\geq$ on it.
2. $E_H = \lbrace \lbrace x, y \rbrace : x \succ y \text{ and } x,y \in P  \rbrace$ \
   We say that "$x$ covers $y$" or $x \succ y$ iff $x \geq y$ and $\nexists z \in P$ such that $x > z > y$.
Note: Observe that point 2 above looks very similar to the simplicial collapse definition we saw in Part I of blog. 

Now that we have a graph associated to the poset $P$, we can now define **partial matching in the poset** $P$ as partial matching in $H(P)$

**Combining all information**\
$\mathcal{K}$ is an abstract simplicial complex with $\sigma, \tau \in \mathcal{K}$ such that the following conditions are satisfied:
1. $\tau$ is a boundary simplex of $\sigma$ of codimension $1$ i.e.  
2. The only simplices in $\mathcal{K}$ that contain $\tau$ are $\tau$ and $\sigma$.
  $$
\nexists \gamma \in \mathcal{K} such that \sigma \superset \gamma \superset \tau
  $$
Removing simplices $\sigma$ and $\tau$ from $\mathcal{K}$ is called an **elementary simplicial collapse**. Clearly, if $(\sigma, \tau)$ is a simplicial collapse, then it correponds to an edge in the graph $H(P)$ where $P = \mathcal{H}(\mathcal{K})$.

Following is a summary of everything discussed above














[^1]: Bauer, U., and Edelsbrunner, H. (2016), "[The Morse theory of Čech and Delaunay complexes](https://doi.org/10.1090/tran/6991)", Transactions of the American Mathematical Society, American Mathematical Society (AMS).
[^2]: Dmitry N. Kozlov (2020), "[Organized Collapse: An Introduction to Discrete Morse Theory](https://www.maa.org/press/maa-reviews/organized-collapse-an-introduction-to-discrete-morse-theory)", Graduate Studies in Mathematics, American Mathematical Society (AMS).
