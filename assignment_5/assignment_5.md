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
We show that MAX CUT is $𝐍𝐏$-complete for simple graphs by reduction from NAESAT to MAX CUT. Simple graph do not have any multiedges or self-loops.

---

We have NAESAT formula $ϕ$ with $n$ variables $\{x_1,...,x_n\}$ and $m$ clauses $\{C_1,...,C_m\}.$

1) Literals $x_i$ and $¬x_i$ in $ϕ$ cannot be in the same truth assignment.

2) Let $α∨β∨γ$ be a clause in $ϕ$. Then, literals $α,β,γ$ cannot all be in the same truth assignment.

We will construct a simple graph $G_ϕ=(V,E)$ as follows.

We create the set of vertices $V$ such that for each literal $x_1,...x_n,¬x_1,...,¬x_n$ we create $3m$ the literals

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

All literals in each row are required to have the same truth assignment.

We crate the set of edges $E$:

1) Add edge between literals $x_{i,j}$ and $¬x_{i,j}$ for each $i=1,...,n$ and $j=1,...,3m.$

2) Add edges $(α_j,β_j)$, $(α_j,γ_j)$ and $(β_j,γ_j)$ for each $j=1,...,m$ where $j$th clause is $C_j=α_j∨β_j∨γ_j$ and
    * $α_j∈\{x_{i,3j-2},¬x_{i,3j-2} ∣ i=1,...,n\}$, 
    * $β_j∈\{x_{i,3j-1},¬x_{i,3j-1} ∣ i=1,...,n\}$, 
    * $γ_j∈\{x_{i,3j},¬x_{i,3j} ∣ i=1,...,n\}$

Now a cut $(S,V-S)$ of size $5m$ in $G_ϕ$ corresponds to a truth assignment satisfying $ϕ$ in the sense of NAESAT.


# H5.2


# H5.3


<!-- # References -->