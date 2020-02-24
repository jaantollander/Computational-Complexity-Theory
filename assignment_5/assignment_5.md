---
title: "Problem Set 5"
date: \today
author: "Jaan Tollander de Balsch"
bibliography: "bibliography.bib"
csl: "https://raw.githubusercontent.com/citation-style-language/styles/master/harvard-anglia-ruskin-university.csl"
link-citations: true
urlcolor: "blue"
---
# H5.1
We show that MAX CUT is $𝐍𝐏$-complete for simple graphs by reduction from NAESAT to MAX CUT. A simple graph does not have any multi-edges or self-loops.

---

We have NAESAT formula $ϕ$ with $n$ variables $\{x_1,...,x_n\}$ and $m$ clauses $\{C_1,...,C_m\}.$

1) Literals $x_i$ and $¬x_i$ in $ϕ$ cannot be in the same truth assignment.

2) Let $α∨β∨γ$ be a clause in $ϕ$. Then, literals $α,β,γ$ cannot all be in the same truth assignment.

We will construct a simple graph $G_ϕ=(V,E)$ as follows.

We create the set of vertices $V$ such that for each literal $x_1,...x_n,¬x_1,...,¬x_n$ we create $3m$ the literals, one for each possible location in the set of clauses.

$$
V = \left\{
\begin{aligned}
x_{1,1},&...,x_{1,3m}, \\
&..., \\
x_{n,1},&...,x_{n,3m}, \\
¬x_{1,1},&...,¬x_{1,3m}, \\
&..., \\
¬x_{n,1},&...,¬x_{n,3m} \\
\end{aligned}
\right\}.
$$

<!-- All literals in each row are required to have the same truth assignment. -->

We create the set of edges $E$ such that for each $j=1,...,m$ where $j$th clause is $C_j=α_j∨β_j∨γ_j$ and

* $α_j∈\{x_{i,3j-2},¬x_{i,3j-2} ∣ i=1,...,n\}$, 
* $β_j∈\{x_{i,3j-1},¬x_{i,3j-1} ∣ i=1,...,n\}$, 
* $γ_j∈\{x_{i,3j},¬x_{i,3j} ∣ i=1,...,n\}$.

1) Add edges $(α_j,¬α_j)$, $(β_j,¬β_j)$ and $(γ_j,¬γ_j)$ to enforce that a literal and its negation are not in the same truth assignment.

2) Add edges $(α_j,β_j)$, $(α_j,γ_j)$ and $(β_j,γ_j)$ to enforce that not all literals are in the same truth assignment.

Now a cut $(S,V-S)$ of size $5m$ in $G_ϕ$ corresponds to a truth assignment satisfying $ϕ$ in the sense of NAESAT.


# H5.2
We show that CLIQUE COVER is $𝐍𝐏$-complete by reduction from GRAPH COLORING to CLIQUE COVER.

---

Given simple graph $G=(V,E)$ its complement graph is $H=(V,E')$ where $E'=(V×V)∖E,$ that is, vertices are adjacent in $H$ if an only if they are not adjacent in $G.$

Deciding graph coloring of at most $K$ colors in $G$ reduces to deciding clique cover of at most $K$ cliques in $H.$ Each clique corresponds to unique color, and all vertices in a clique have the same color.

Proof: 

1) If $(u,v)∈E$, vertices $u$ and $v$ must have different colors in $G$. Then $(u,v)∉E'$, vertices $u$ and $v$ must belong to different cliques in $H$.

2) If $(u,v)∉E$, vertices $u$ and $v$ can have the same colors in $G$. Then $(u,v)∈E'$, vertices $u$ and $v$ can belong to the same clique in $H$.


# H5.3
Set cover problem

* SET COVER
* INSTANCE: A family $F=\{S_1,...,S_n\}$ of subsets of a finite set $U$ and an integer $B.$
* QUESTION: Is there a subfamily of $≤B$ sets in $F$ whose union is $U?$

---

Formalization of the mention all problem.

* MENTION ALL
* INSTANCE: Families $F'=\{S'_1,...,S'_n\}$ and $F''=\{S''_1,...,S''_n\}$ of subsets of a finite set $U.$
* QUESTION: Is there subfamily $\{S_1,...,S_n\}$ where $S_i∈\{S'_i,S''_i\}$ for all $i=1,...,n$ whose union is $U?$

---

Generalization of MENTION ALL

* MENTION $k$-ALL
* INSTANCE: Families $F^1=\{S^1_1,...,S^1_n\}, ..., F^k=\{S^k_1,...,S^k_n\}$ of subsets of a finite set $U$ where $k≥2$ is integer.
* QUESTION: Is there subfamily $\{S_1,...,S_n\}$ where $S_i∈\{S_i^1,...,S_i^k\}$ for all $i=1,...,n$ whose union is $U?$

---

Reduction from SET COVER to MENTION $k$-ALL.

We can set $F^1=...=F^B=F$ to reduce *set cover* to *mention $k$-all*.

---

Reduction from MENTION $k$-ALL to MENTION ALL.

<!-- If $k$ is odd we pad the input with $F^{k+1}=\{∅,...,∅\}.$ -->

If the recursive step of *mention all*, we set the elements in the subset families as follows. For all $i=1,...,n$:

* $S_i'=S_1^1∪...∪S_i^{⌊k/2⌋}$
* $S_i''=S_i^{⌊k/2⌋+1}∪...∪S_i^{k}$

After the iteration we have solution $S_i∈\{S_i',S_i''\}$ if it exists. Each recursive step splits the subsets forming the union.

We repeat the recursive step if solution exists until each subset $S_i$ is of of the subsets $\{S_i^1,...,S_i^k\}.$ It takes $\log_2 k$ iterations.

<!-- # References -->
