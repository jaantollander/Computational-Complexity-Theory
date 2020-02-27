---
title: "Problem Set 6"
date: \today
author: "Jaan Tollander de Balsch"
bibliography: "bibliography.bib"
csl: "https://raw.githubusercontent.com/citation-style-language/styles/master/harvard-anglia-ruskin-university.csl"
link-citations: true
urlcolor: "blue"
---
# H6.1
We define the cumulative polynomial time hierarchy as follows.

$$Σ_0^p=𝐏,\quad Σ_{k+1}^p=𝐍𝐏^{Σ_k^p},\quad 𝐏𝐇 = ⋃_{k≥0}Σ_k^p.$$

Lets prove that

$$\mathbf{PH} ⊆ \mathbf{PSPACE}.$$

---

We will use induction to prove that $Σ_k^p⊆\mathbf{PSPACE}$ for all $k≥0.$

*Base step*: Let prove that statement holds for $k=0.$

$$Σ_0^p=𝐏⊆\mathbf{PSPACE}.$$

*Inductive step*: Assuming that the statement holds for $k,$ we have

$$Σ_k^p⊆\mathbf{PSPACE}.$$

Then the statement for $k+1$ is

$$Σ_{k+1}^p=𝐍𝐏^{Σ_k^p}⊆\mathbf{NPSPACE}=\mathbf{PSPACE}$$

By *Savitch's theorem*, deterministic and nondeterministic polynomial spaces are equivalent.


# H6.2


# H6.3


<!-- # References -->