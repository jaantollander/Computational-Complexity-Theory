---
title: "Problem Set 2"
date: \today
author: "Jaan Tollander de Balsch"
bibliography: "bibliography.bib"
csl: "https://raw.githubusercontent.com/citation-style-language/styles/master/harvard-anglia-ruskin-university.csl"
link-citations: true
urlcolor: "blue"
---
# H2.1
We have languages $A$ and $B$ in $\mathbf{NP}$, which means that nondeterministic Turing machines can decide them in polynomial time. We will denote these Turing machines using $N_A$ and $N_B$.

## Union
Input $x∈A∪B$ implies $x∈A$ or $x∈B$. We define nondeterministic Turing machine $N$ as follows:

> $N(x)$: if $x∈A$ return $N_A(x)$ else if $x∈B$ return $N_B(x)$

Then, for all inputs $x∈A∪B$, $x$ is decided by $N$ in polynomial time. Thus language $A∪B$ is in $\mathbf{NP}$.

## Intersection
Since $A∩B⊆A∪B$, the language $A∩B$ is also decided by $N$ in polynomial time.  Therefore, it is in $\mathbf{NP}$.

# H2.2
Need to show that $\mathbf{NP}⊆\mathbf{PSPACE}$ and $\mathbf{PSPACE}⊆\mathbf{EXP}$.

---

Nondeterministic Turing machine operating in time polynomial time $n^k$ can write at most a string of length $n^k$, therefore, requiring at most polynomial $n^k$ amount of space.

However, language decided by Turing machine in polynomial space can take more than polynomial time by nondeterministic Turing machine since we can reuse space.

Therefore we have $\mathbf{NP}⊆\mathbf{PSPACE}$.

---

For some Turing machine operating in $n^k$ space, there are $|Σ|^{n^k}$ possible strings. Therefore, the maximum amount of time it can take some Turing machine to decide $L$ is exponential $2^{p(n)}$ for some polynomial $p(n)$, which means going through every string.

A Turing machine operating in exponential time can write strings that take more than polynomial space.

Therefore we have $\mathbf{PSPACE}⊆\mathbf{EXP}$.


# H2.3
Reduce language $L_7$ to language halt $H$.


# References
