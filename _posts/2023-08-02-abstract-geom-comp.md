---
layout: article
title: Abstract and Geometric Simplicial Complexes 
mathjax: true
tags: complexes tda alg_topo
---

### Abstract and Geometric Simplicial complexes
An **abstract simplicial complex** $\mathcal{X}$ is a collection of *finite* sets that are closed under taking subsets. Note that, the empty set $\emptyset$ is assumed to lie in $\mathcal{X}$. Although each element of the abstract simplicial complex must be a finite set, the cardinality of the complex in itself need not be finite, or even countable. The elements of the complex $\mathcal{X}$ are called **simplices**. \
The **vertices** of $\mathcal{X}$ are defined as the simplices that are singleton sets. The notation $\mathcal{X}_0$ is used to denote the set of all vertices. Again, the set $\mathcal{X}_0$ can be finite, countable, or even uncontable[^2]. The **dimension** of a simplex $\sigma$ is defined as $|\sigma| - 1$ i.e. one less than the cardinality of $\sigma$. Dimension of the complex $\mathcal{X}$ is the largest dimension among all simplicies. The subsets of a simplex are called **faces**, which also belong to $\mathcal{X}$ by definition. 

**Example 1:** An *undirected graph* $G = (V, E)$ with vertex and edge sets given by $V$ and $E$ respectively is actually a 1-dimensional abstract simplicial complex made up of 0-simplices contained in $V$ and 1-simplices in $E$. From the point of view of modeling interactions in a real-world process, an undirected graph can only capture up to pairwise interactions. On the other hand, an abstract simplicial complex generalizes a graph in the sense that it can model higher dimensional interactions as well.[^3]

**Example 2:** A set system $(E, \mathcal{F})$ is an **Independence System** if it is a [hypergraph](https://encyclopediaofmath.org/wiki/Hypergraph) satisfying the following conditions[^5]:
* $\emptyset \in \mathcal{F}$;
* If $W \subseteq Y \in \mathcal{F}$ then $W \in \mathcal{F}$.
The elements of $\mathcal{F}$ are called *independent* while the elements of $2^E-\mathcal{F}$ are *dependent*. Clearly, the independence system is also a well-defined simplicial complex. It is also called the **independence complex**. An independence complex encodes the statistical dependencies between a finite set of random variables in a compact manner.

Hypergraphs need not always define a simplicial complex. However, **matroids**, which is a special case of the independence system is also a well-defined simplicial complex. Matroids are a generalization of matrices. Therefore, it makes sense that graphical models are often summarized as a matrix. The correspondence between matrices and graphs (hypergraphs) is not discussed in detail here.

**Example 3:** BIBD

**Example 4:** Network
network vs hypergraph vs simplicial complex vs graph

A **Geometric simplicial complex** $\mathcal{K}$  also called a **triangulation** is a set containing *finitely* many geometric simplices, which are defined as the convex hull of affinely independent points in Euclidean space, which are closed under taking subsets. Abstract simplicial complexes are useful to understand the combinatorial structure of a topological space. However, the geometric simplicial complexes associated with the abstract complexes (up to isomorphism) can help reveal other interesting properties of the underlying topological space.

A geometric simplicial complex $\mathcal{K}_e$ is called the **geometric realization** of an abstract complex $\mathcal{X}$  *iff* for "sufficiently large" $m$ there is an (injective) embedding $e: \mathcal{X}_0 \longrightarrow \mathbb{R}^m$ that takes every simplex $\lbrace v_0, v_1, \cdots, v_k  \rbrace \in \mathcal{X}$ to a geometric k-simplex $\mathrm{conv}( \text{ } e(v_0), e(v_1) \cdots, e(v_k) \text{ })$ in $\mathbb{R}^m$.

**Theorem:** Every abstract simplicial complex $\mathcal{X}$ of dimension $d$ has a geometric realization $\mathcal{K}$ in $\mathbb{R}^{2d + 1}$.[^6]

For every abstract simplicial complex $\mathcal{X}$ there is a triangulation, unique up to an isomorphism, whose simplicial complex is $\mathcal{X}$.

Check simplicial complex vs underlying space


[^1]: Course [MATH0074: Topology and Groups (2017)](https://www.homepages.ucl.ac.uk/~ucahjde/tg/html/index.html) taught by [Prof. Jonny Evans](http://jde27.uk/) at University College London, UK.
[^2]: Nov 9 notes under "Complexes and Homology", [CS598: Computational Topology (Fall 09)](https://jeffe.cs.illinois.edu/teaching/comptop/2009/schedule.html), Lecture notes by [Prof. Jeff Erickson](https://jeffe.cs.illinois.edu/index.html), Dept. of Computer Science, UIUC, Viewed on 07/28/2023.
[^3]: Ch2: Complexes, R. Ghrist, ["Elementary Applied Topology"](https://www2.math.upenn.edu/~ghrist/notes.html), ed. 1.0, Createspace, 2014.
[^4]: [Hypergraph](https://encyclopediaofmath.org/wiki/Hypergraph). Encyclopedia of Mathematics.
[^5]: Bernhard Korte and Jens Vygen. 2018. [Combinatorial Optimization: Theory and Algorithms](https://doi.org/10.1007/978-3-662-56039-6) (6th. ed.). Springer Berlin, Heidelberg.
[^6]: Harer
[^7]: Tamal
