---
layout: article
title: Discrete Morse Theory - I
mathjax: true
tags: morse_theory intro alg_topo
---

The blog introduces terms and results from Discrete Morse Theory that will eventually be helpful in understanding the paper **The Morse Theory of Cech and Delaunay Complexes** by U. Bauer and H. Edelsbrunner[^1]. The textbook I adhered to learn the basics is the textbook "**Organized Collapse: An Introduction to Discrete Morse Theory**" by Dmitry N. Kozlov[^2]. Additionally, Robin Forman's "A User's Guide To Discrete Morse Theory"[^3] is a very concise and useful introduction to Discrete Morse Theory.

Firstly, Morse Theory is unrelated to Morse code although the pioneering people involved are  Marston Morse and Samuel Morse respectively. As the title suggests, discrete Morse theory is the "discretized" version of a branch of mathematics called Morse theory. A simple visual introduction to Morse Theory is given in the blog by Prof. Bastian Rieck titled "A visual introduction to Morse theory"[^4]. In addition to this, the preface in the book by Dmitry N. Kozlov[^2] provides a good motivation behind the discrete Morse theory.

### Elementary Simplicial Collapse
Intuitively, an elementary simplicial collapse is a structured way of removing two simplices such that the resulting complex is still an abstract simplicial complex. The mathematical definition below explains the structured way of removing simplices.

$\mathcal{K}$ is an abstract simplicial complex with $\sigma, \tau \in \mathcal{K}$ such that the following conditions are satisfied:
1. $\tau$ is a boundary simplex of $\sigma$ of codimension $1$ i.e.

  $$
  \partial_k (\sigma) = \tau \text{ where } \partial_k: C_k \longrightarrow C_{k-1} \text{ is the boundary operator.}
  $$
  
2. The only simplices in $\mathcal{K}$ that contain $\tau$ are $\tau$ and $\sigma$.

Removing simplices $\sigma$ and $\tau$ from $\mathcal{K}$ is called an **elementary simplicial collapse**.

**Remarks:** 
* Elementary simplicial collapses are mostly abbreviated as *simplicial collapse* unless otherwise specified.
* The definition above claims that the simplex $\sigma$ must be *maximal*[^5] in the sense that it is not the proper face of any other simplex in $\mathcal{K}$.
  $$
  \sigma \quad \text{ is maximal iff } \quad \nexists \quad \gamma \in \mathcal{K} \quad \text{such that} \quad \sigma \subset \gamma
  $$
* The simplex $\tau$ is called **free simplex**. Clearly, if $\mathcal{K}$ does not contain any free simplices, then simplicial collapse is not possible.
* $\mathcal{K} \setminus \lbrace \sigma, \tau \rbrace $, the set of sets obtained after a simplicial collapse, can be proved to be a well-defined simplicial complex.[^2]

### Example
The following is an illustration of a simplicial collapse drawn using [Inkscape](https://inkscape.org/).

![collapse](\images\example_collapse.svg)

The following observations can be made based on the simple example above.
1. There can be more than one possible sequence of elementary collapses for a given simplicial complex $\mathcal{K}$. In fact, different sequences of collapses can lead to non-isomorphic subcomplexes.
2. The order in which we perform collapses is important as well. If we follow the "wrong order" of collapses, then we will end up with a non-collapsible subcomplex very early on.

### Void Simplicial complex
A void simplicial complex $\mathcal{K}$ is an empty set i.e. it doesn't even include the empty simplex $\emptyset$. Hence $\mathcal{K} = \lbrace \quad \rbrace$. \
Consider a vertex or a 0-complex $\mathcal{K}_1 = \lbrace \emptyset, \lbrace v \rbrace  \rbrace$. Here, the empty simplex $\emptyset$ is considered free. Hence $\mathcal{K}_1$ to  $\lbrace \rbrace$ is a *valid elementary collapse*. However, the empty simplicial complex $\lbrace \emptyset \rbrace$ is *not* collapsible.

### Collapsible simplicial complex
* An abstract simplicial complex $\mathcal{K}$ is called **collapsible** if there exists a sequence of (elementary) simplicial collapses reducing $\mathcal{K}$ to the void simplicial complex.
* Following a sequence of simplicial collapses on $\mathcal{K}_1$, we get another simplicial complex $\mathcal{K}_2$. Then we say *$\mathcal{K}_1$ can be collapsed to $\mathcal{K}_2$*.
  $$
  \text{Notation: } \mathcal{K}_1 \searrow \mathcal{K}_2
  $$
**Remark**: Collapsibility is a transitive relation i.e. $\mathcal{K}_1 \searrow \mathcal{K}_2$ and $\mathcal{K}_2 \searrow \mathcal{K}_3 \quad \implies \mathcal{K}_1 \searrow \mathcal{K}_3$.

### Deformation Retracts
![topo](\images\topo.svg)

$X$ is a topological space with $A \subset X$ and $i: A \hookrightarrow X$ denotes the inclusion map. Let $f: X \rightarrow A$ be a continuous map. The notation $\mathcal{I}_S$ is used to denote the identity map on set $S$. Then:
1. $f: X \rightarrow A$ is a **retraction** and $A$ is called a **retract** of $X$ if $f \vert_A \equiv i \circ f = \mathcal{I}_A$ i.e. $f(a) = a \quad \forall \quad a \in A$.
   
   ![retract](\images\retract.svg)
   
3. $f: X \rightarrow A$ is a **deformation retraction** and $A$ is called a **deformation retract** of $X$ if $i \circ f \simeq \mathcal{I}_X$. Intuitively, $f \vert_A$ can be *continuously deformed* to give   $\mathcal{I}_X$.
   
   ![dretract](\images\def_retract.svg)
   
4. $f: X \rightarrow A$ is a **strong deformation retraction** and $A$ is called a ** strong deformation retract** of $X$ if $i \circ f \simeq \mathcal{I}_X$ via the homotopy map $F: X \times I \rightarrow X$ such that $F(a,t) = a$ for all $a \in A$ and $t \in I$. Intuitively, we  can continuously deform $f \vert_A$ to give $\mathcal{I}_X$ such that the deformation process parameter $t$ is independent of the homotopy map value.
   Example: $A = \mathcal{S}^1 = \lbrace x \in \mathbb{R}^2 : \| x \| = 1  \rbrace$ is a strong deformation retraction of $X = \mathbb{R}^2 \setminus \lbrace 0 \rbrace$.
   
  ![sdretract](\images\strong_def.svg)
  
### Simplicial collapse as strong deformation retracts.
**Proposition:**[^2] $\mathcal{K}$ is a simplicial complex with $\sigma, \tau \in \mathcal{K}$ such that $\mathrm{dim} \sigma = \mathrm{dim} \tau + 1 \geq 1$. Simplicial collapse corresponding to $\sigma, \tau$ yields a strong deformation retract of $A = \mathrm{Geom}(\mathcal{K}\setminus \lbrace \sigma, \tau \rbrace)$ on $X = \mathrm{Geom}(\mathcal{K})$ where $\mathrm{Geom}(\cdot)$ represents geometric realization of simplicial complex. \
**Proof:** Refer Pg. 152-153, proposition 9.9, of the textbook by D. Kozlov [^2]. A simple example of viewing simplicial collapse as a strong deformation retract is given below. Observe how the Geometric realization of $\mathcal{K} \setminus \lbrace \sigma, \tau \rbrace$ is fixed throughout the deformation process.

![ef](\images\pic_proof.png)

### Compound collapse
$\mathcal{K}$ is an abstract simplicial complex with $\sigma, \tau \in \mathcal{K}$ such that:
* $\tau \subset \sigma$ and $\mathrm{dim}(\tau) < \mathrm{dim}(\sigma)$.
* Every simplex containing $\tau$ must be contained in $\sigma$ i.e.
  $$
  \text{ If } \tau \subset \gamma \text{ then } \gamma \in \sigma ; \quad \gamma \in \mathcal{K} 
  $$
A **compound simplicial collapse** of $\mathcal{K}$ is the removal of all simplices $\gamma$ such that $\tau \subset \gamma \subset \sigma$.

**Remarks:** 
1. Compound collapse is a generalization of the concept of elementary simplicial collapse in the sense that the difference between the dimensions of $\sigma$ and $\tau$ is strictly more than $1$.
2. In case of an elementary simplicial collapse, if there exists a simplex $\gamma$ satisfying $\tau \subset \gamma \subset \sigma$, then $\tau = \gamma$.
3. In short, we call the pair $(\sigma, \tau)$ a compound simplicial collapse.

Intuitively, we would expect a compound simplicial collapse to be made up of a sequence of elementary simplicial collapses. Proposition 9.18 from D. N. Kozlov[^2] textbook gives rigorous proof to the statement of this statement of interest.

**Corollary[^2] :** A sequence of compound collapses from a complex $\mathcal{K}_1$ to a complex $\mathcal{K}_2$ yields a strong deformation retract of $A = \mathrm{Geom}(\mathcal{K}_2)$ on $X = \mathrm{Geom}(\mathcal{K}_1)$.

**Proof:** Refer to Corollary 9.19 in Kozlov's textbook.

**Special Case:** If $\mathcal{K}_1$ is a collapsible complex, then taking $\mathcal{K}_2 = \lbrace \quad \rbrace$, we conclude that $\mathrm{Geom}(\mathcal{K}_1)$ is contractible i.e. it is homotopic to a point (also called null-homotopy).

$$
\mathcal{K}_1 \text{ collapsible } \implies \mathrm{Geom}(\mathcal{K}_1) \text{ is contractible}
$$

However, the converse need not be true i.e. there are simplicial complexes that are not collapsible but have a contractible geometric realization.

$$
\mathcal{K}_1 \text{ collapsible } \nLeftarrow \mathrm{Geom}(\mathcal{K}_1) \text{ is contractible}
$$

Theorem 9.24 of Kozlov's textbook states that the converse, and hence the equivalence, holds i.e. $\mathrm{Geom}(\mathcal{K}_1)$ is contractible if there exists collapsible $\tilde{\mathcal{K}_1}$ such that $\mathcal{K}_1 \subset \tilde{\mathcal{K}_1}$ and $\tilde{\mathcal{K}_1} \searrow \mathcal{K}_1$. This result is the motivation behind the concept of "simplicial expansion" which is defined in the next section.

### Simple Homotopy Theory
Assume simplicial complexes $\mathcal{K}$ and $\mathcal{K'}$ such that $\mathcal{K} \searrow \mathcal{K'}$ via an elementary collapse. Then $\mathcal{K}$ is said to be obtained from $\mathcal{K'}$ via an **elementary simplicial expansion** or just simplicial expansion. Note that simplicial expansions are also called **anti-collapses**. The notation used for this is $\mathcal{K'} \nearrow \mathcal{K}$.

$$
\mathcal{K} \searrow \mathcal{K'} \text{ is an elementary collapse } \Longleftrightarrow \mathcal{K'} \nearrow \mathcal{K} \text{ is an elementary expansion. }
$$

Simplicial expansion, like a simplicial collapse, can be decomposed as a sequence of elementary simplicial expansions. Now, coming back to Theorem 9.24, we can claim that $(\mathcal{K})$ is collapsible if:

$$
\exists \mathcal{K'} \supseteq \mathcal{K} \text{ such that } \mathcal{K'} \searrow \mathcal{K} \text{ given that } \mathcal{K} \text{ is collapsible i.e. } \mathcal{K}\searrow \lbrace v \rbrace \text{ for some } v \in \mathcal{K}^0
$$

Two abstract simplicial complexes are said to have the same **simple homotopy type** if there exists a sequence of elementary collapses and expansions leading from one to another. Such a sequence is called a **formal deformation**.

[^1]: Bauer, U., and Edelsbrunner, H. (2016), "[The Morse theory of Čech and Delaunay complexes](https://doi.org/10.1090/tran/6991)", Transactions of the American Mathematical Society, American Mathematical Society (AMS).
[^2]: Dmitry N. Kozlov (2020), "[Organized Collapse: An Introduction to Discrete Morse Theory](https://www.maa.org/press/maa-reviews/organized-collapse-an-introduction-to-discrete-morse-theory)", Graduate Studies in Mathematics, American Mathematical Society (AMS).
[^3]: Forman, Robin. "[A user's guide to discrete Morse theory.](http://eudml.org/doc/123837)", Séminaire Lotharingien de Combinatoire [electronic only] 48 (2002): B48c, 35 p., electronic only-B48c, 35 p., electronic only.
[^4]: ["A visual introduction to Morse theory"](https://bastian.rieck.me/blog/posts/2019/morse_theory/) Blog post by Prof. Bastian Rieck.
[^5]: Nov 9 notes under "Complexes and Homology", [CS598: Computational Topology (Fall 09)](https://jeffe.cs.illinois.edu/teaching/comptop/2009/schedule.html), Lecture notes by [Prof. Jeff Erickson](https://jeffe.cs.illinois.edu/index.html), Dept. of Computer Science, UIUC, Viewed on 08/18/2023. 
