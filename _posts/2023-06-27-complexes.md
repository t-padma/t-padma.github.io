---
layout: article
title: Simplicial Complexes
mathjax: true
tags: intro tda
---

The contents of this post are predominantly based on the review paper by Otter et al. [^1] which discusses the computational aspects of Persistent Homology (PH). To begin with, the first four sections of the paper give a very good introduction to TDA without getting lost in unnecessary mathematical details. I believe that this can serve as a first introduction to PH for anyone who later wishes to understand PH with proper mathematical rigor. However, in the current post, I would like to focus on the first half of section five which familiarizes the reader with some of the **simplicial complexes** used while working with *point-cloud data*.

TDA deals with data that can be viewed as *finite metric spaces*. Such data sets are also referred to as point-cloud data sets. For instance, networks and digital images can be modeled as finite metric spaces. I found the lecture notes by [Prof. Vidit Nanda](https://people.maths.ox.ac.uk/nanda/)[^2] to be extremely helpful while learning some basics of computational topology. The article by Lazar and Ryu[^3] does a really good job of giving the big picture for TDA. Now, given a finite set of points, we wish to encode the ``shape" information of the data into a simplicial complex which is much easier to handle mathematically. Simplicial complexes give us the benefit of exploiting the well-understood field of simplicial homology which is known to be better in terms of computations. 

*Notations used in the post:* $K$ is the simplicial complex on vertex set $S$ such that $|S| < \infty$. Note that $\sigma = \langle v_{j_0},  \cdots, v_{j_p}\rangle$ denotes a p-simplex in $K$ i.e. $\sigma$ is the convex hull associated with the vertices $\lbrace v_{j_0}, \cdots, v_{j_p} \rbrace \subset S$. We use the notation $K_i$ to denote the set of all $i$-dimensional simplices in $K$. We assume that $S$ lies inside an unknown metric space $(X,d)$ such that $(S,d)$ is an induced metric space.  

**Big picture:** Persistent homology is a tool that allows the encoding of shape information at different scales. At each individual scale value, we need to associate the shape information in the form of a simplicial complex. Finite metric spaces are not topologically interesting[^4], hence we try to "fill in the gaps" between points if they are "close enough". That way we can impose topological structures onto the data.[^5] The idea is that if we build a simplicial complex $K$ on set $S$, then the homology of $K$ has to at least ``approximate" the homology of $X$. Hence the choice of how to construct the simplicial complex matters. 

### $\check{\mathcal{C}}(S; \epsilon)$: Cech complex at scale $\epsilon \> 0$ 
Given a fixed positive $\epsilon \in \mathbb{R}$, the **Aleksandrov-Cech** complex, also commonly known as the **Cech complex**, at scale $\epsilon$ is defined as the **intersection complex** or **nerve** of the $\epsilon$-balls associated with set $S$. The resource [Cech Complex playground](https://sauln.github.io/blog/nerve-playground/) is a useful visualization tool. The Cech complex, denoted by $\check{\mathcal{C}}(S, \epsilon)$, is defined as follows:

$$
\check{\mathcal{C}}(S; \epsilon) = \left\lbrace  \langle v_{j_0}, \cdots, v_{j_p} \rangle \subset S \quad : \quad \bigcap_{z=0}^p \mathcal{B}(v_{j_z}; \epsilon) \neq \emptyset \right\rbrace
$$



### Delaunay complex

### Alpha Complex

### Witness complex















[^1]: Otter, N., Porter, M.A., Tillmann, U. et al. [*A roadmap for the computation of persistent homology*](https://doi.org/10.1140/epjds/s13688-017-0109-5). EPJ Data Sci. 6, 17 (2017). 
[^2]: [Computational Algebraic Topology](https://people.maths.ox.ac.uk/nanda/cat/), Lecture notes by Prof. Vidit Nanda, Mathematical Institute, University of Oxford.
[^3]: Nicole Lazar & Hyunnam Ryu (2021) The Shape of Things: Topological Data Analysis, CHANCE, 34:2, 59-64, DOI: 10.1080/09332480.2021.1915036
[^4]: [A finite topological space is metrizable iff it is discrete](https://math.stackexchange.com/questions/3367163/a-finite-topological-space-is-metrizable-iff-it-is-discrete), Math StackExchange
[^5]: Nov 11 notes under "Complexes and Homology", [CS598: Computational Topology (Fall 09)](https://jeffe.cs.illinois.edu/teaching/comptop/2009/schedule.html), Lecture notes by [Prof. Jeff Erickson](https://jeffe.cs.illinois.edu/index.html), Dept. of Computer Science, UIUC, Viewed on 06/27/2023. 



