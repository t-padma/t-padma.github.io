---
layout: article
title: Simplicial Complexes
mathjax: true
tags: intro tda
---

### Introduction and Motivation
The contents of this post are predominantly based on the review paper by Otter et al. [^1] which discusses the computational aspects of Persistent Homology (PH). To begin with, the first four sections of the paper give a very good introduction to TDA without getting lost in unnecessary mathematical details. I believe that this can serve as a first introduction to PH for anyone who later wishes to understand PH with proper mathematical rigor. However, in the current post, I would like to focus on the first half of section five which familiarizes the reader with some of the **simplicial complexes** used while working with *point-cloud data*.

TDA deals with data that can be viewed as *finite metric spaces*. Such data sets are also referred to as point-cloud data sets. For instance, networks and digital images can be modeled as finite metric spaces. The lecture notes by [Prof. Vidit Nanda](https://people.maths.ox.ac.uk/nanda/)[^2] were extremely helpful in learning some basics of computational topology. The article by Lazar and Ryu[^3] does a really good job of giving the big picture for TDA. Now, given a finite set of points, we wish to encode the "shape" information of the data into a simplicial complex which is much easier to handle mathematically. Simplicial complexes give us the benefit of exploiting the well-understood field of simplicial homology which is known to be better in terms of computations. 

**Notations used in the post:**
Let $S$ be the finite dataset (also a metric space) at hand. $K$ is the simplicial complex on vertex set $S$ with $|S| < \infty$. Note that $\sigma = \langle v_{j_0},  \cdots, v_{j_p}\rangle$ denotes a $p$-simplex in $K$ i.e. $\sigma$ is the convex hull associated with the vertices $\lbrace v_{j_0}, \cdots, v_{j_p} \rbrace \subset S$. We use the notation $K_i$ to denote the set of all $i$-dimensional simplices in $K$. We assume that the data set $S$ lies inside an unknown metric space $(X,d)$ such that $(S,d)$ is an induced metric space.  

**Big picture:** Persistent homology is a tool that allows the encoding of shape information at different scales. At each scale value, we need to store the shape information in the form of a simplicial complex. Finite metric spaces are not topologically interesting[^4], hence we try to "fill in the gaps" between data points if they are "close enough" in some sense. That way we will be able to impose topological structures onto the data.[^5] The idea is that if we build a simplicial complex $K$ on set $S$, then the homology of $K$ has to at least ``approximate" the homology of $X$. Hence the choice of how to construct the simplicial complex matters. 

### $\check{\mathcal{C}}(S; \epsilon)$: Cech complex at scale $\epsilon \> 0$ 
Given a fixed positive $\epsilon \in \mathbb{R}$, the **Aleksandrov-Cech** complex, also commonly known as the **Cech complex**, at scale $\epsilon$ is defined as the **intersection complex** or **nerve** of the $\epsilon$-balls associated with set $S$. The resource [Cech Complex playground](https://sauln.github.io/blog/nerve-playground/) is a useful visualization tool. The Cech complex, denoted by $\check{\mathcal{C}}(S, \epsilon)$, is defined as follows:

$$
\check{\mathcal{C}}(S; \epsilon) = \left\lbrace  \langle v_{j_0}, \cdots, v_{j_p} \rangle \subset S \quad : \quad \bigcap_{z=0}^p \mathcal{B}(v_{j_z}; \epsilon) \neq \emptyset \right\rbrace
$$

The *Nerve Lemma* provides a theoretical guarantee on why the Cech complex is "correct". There are different versions of the Nerve Lemma, but all of them have a similar idea which is given below[^6].

Let $\mathcal{A} = \lbrace A_1, \cdots, A_m \rbrace$ be a family of "nice" subsets covering a space Euclidean $X$ such that all possible intersections are "topologically simple", then the topology of the nerve agrees with the topology of $X$ in certain ways. Despite the advantage of the Nerve Lemma, the Cech complex is not widely used due to a lack of computational feasibility.

Assume $\|S\| = n$, then the worst case size (i.e. cardinality of the set $K$) of the simplicial complex associated with data is $\mathcal{O}(2^n)$. The number of steps required to associate the data to a simplicial complex is also $\mathcal{O}(2^n)$ since we have to check the intersection of all possible collections of simplices in $K$.

### $\mathcal{VR}(S; \epsilon)$: Vietoris-Rips complex at scale $\epsilon \> 0$
When homology theory was still new, Leopold Vietoris used a complex that is similar to the Vietoris-Rips complex to model metric spaces using finite simplicial complexes. The Vietoris-Rips complex, often called the Rips complex, is now commonly used in TDA due to its computational benefits over the Cech complex. The Rips complex associated with the dataset $S$ is defined as follows:

$$
\mathcal{VR}(S; \epsilon) = \left\lbrace \sigma \subseteq S \quad : \quad \mathrm{d}(x,y) \leq 2\epsilon \quad \forall x,y \in \sigma \right\rbrace
$$

Given any $\epsilon > 0$, the Rips complex is said to approximate the Cech complex because the Rips complex at scale $\epsilon$ can be "sandwiched" between Cech complexes at scales $\epsilon$ and 2 $\epsilon$. These bounds cannot be improved if $X$ is assumed to be an arbitrary metric space. The upper radius can be improved to $\frac{\sqrt{3}\epsilon}{2}$ if the underlying space $X$ is Euclidean.[^5]

$$
\check{\mathcal{C}}(S; \epsilon) \quad \subseteq \quad \mathcal{VR}(S; \epsilon) \quad \subseteq \quad \check{\mathcal{C}}\left(S; \frac{\sqrt{3}\epsilon}{2} \right) \quad \text{ when underlying metric space is Euclidean}
$$

Assume a $p$-simplex $\sigma \subseteq S$ with $\|S\| = n$, the following are the computational costs associated with Rips and Cech complexes:
* In order to construct $\check{\mathcal{C}}(S; \epsilon)$, we have to check all possible $k$-set intersections for $k = 1,2, \cdots, n$. Observe that there are $n \choose k$ many subsets of $S$ of size $k$. Hence there are $n \choose k$ many intersections that need to be checked. This implies that Cech complex construction takes **exponential time**. On the other hand, it is sufficient to check all possible pairwise intersections to construct the Rips complex. This clearly takes **polynomial time**.
* However, the cardinality of the Cech complex or Rips complex is still **exponential**. This is because the worst case complex is $\mathcal{P}(S)$, powerset of $S$, in either of the two cases. Hence one usually computes the Rips complex up to some dimension $p << n$.

**Rips complex construction**
1. Compute the **proximity graph** or $\epsilon$-**neighbourhood graph**, denoted as $N_{\epsilon}(S)$, associated to the dataset $S$ is a graph $(S, \mathcal{E})$ with edge set defined as

$$ 
\mathcal{E} = \lbrace (i,j) \in S \times S : i \neq j \text{ and } \mathrm{d}(i,j) \leq 2 \epsilon \rbrace 
$$

2. Rips complex is the **clique complex** associated with the proximity graph $N_{\epsilon}(S)$. A clique complex,  also referred to as the **flag complex**, associated with the graph $N_{\epsilon}(S)$ is defined as follows:

$$
\sigma \subseteq S \text{ is a simplex iff the vertices in } \sigma \text{ form a *clique* in }  N_{\epsilon}(S) 
$$



### Delaunay complex

### Alpha Complex

### Witness complex















[^1]: Otter, N., Porter, M.A., Tillmann, U. et al. [*A roadmap for the computation of persistent homology*](https://doi.org/10.1140/epjds/s13688-017-0109-5). EPJ Data Sci. 6, 17 (2017). 
[^2]: [Computational Algebraic Topology](https://people.maths.ox.ac.uk/nanda/cat/), Lecture notes by Prof. Vidit Nanda, Mathematical Institute, University of Oxford.
[^3]: Nicole Lazar & Hyunnam Ryu (2021) The Shape of Things: Topological Data Analysis, CHANCE, 34:2, 59-64, DOI: 10.1080/09332480.2021.1915036
[^4]: [A finite topological space is metrizable iff it is discrete](https://math.stackexchange.com/questions/3367163/a-finite-topological-space-is-metrizable-iff-it-is-discrete), Math StackExchange
[^5]: Nov 11 notes under "Complexes and Homology", [CS598: Computational Topology (Fall 09)](https://jeffe.cs.illinois.edu/teaching/comptop/2009/schedule.html), Lecture notes by [Prof. Jeff Erickson](https://jeffe.cs.illinois.edu/index.html), Dept. of Computer Science, UIUC, Viewed on 06/27/2023. 
[^6]: (2008). A Topological Interlude. In: [Using the Borsuk–Ulam Theorem](https://doi.org/10.1007/978-3-540-76649-0_4). Universitext. Springer, Berlin, Heidelberg. 


