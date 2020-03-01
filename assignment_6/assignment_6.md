---
title: "Problem Set 6"
date: \today
author: "Jaan Tollander de Balsch"
bibliography: "bibliography.bib"
csl: "https://raw.githubusercontent.com/citation-style-language/styles/master/harvard-anglia-ruskin-university.csl"
link-citations: true
urlcolor: "blue"
---
For the theory, we refer to @papa1994.

# H6.1
We define the cumulative polynomial-time hierarchy as follows.

$$Σ_0^p=𝐏,\quad Σ_{k+1}^p=𝐍𝐏^{Σ_k^p},\quad 𝐏𝐇 = ⋃_{k≥0}Σ_k^p.$$

Let us prove that

$$\mathbf{PH} ⊆ \mathbf{PSPACE}.$$

---

We will use induction to prove that $Σ_k^p⊆\mathbf{PSPACE}$ for all $k≥0.$

*Base step*: Let prove that statement holds for $k=0.$

$$Σ_0^p=𝐏⊆\mathbf{PSPACE}.$$

*Inductive step*: Assuming that the statement holds for $k,$ we have

$$Σ_k^p⊆\mathbf{PSPACE}.$$

Then the statement for $k+1$ is

$$Σ_{k+1}^p=𝐍𝐏^{Σ_k^p}⊆\mathbf{NPSPACE}=\mathbf{PSPACE}$$

By *Savitch's theorem*, deterministic and non-deterministic polynomial spaces are equivalent.


# H6.2
For this exercise, we refer to the paper by @McLoughlin1984.

A binary linear code of length $n$:

- *Parity check matrix* $H∈\{0,1\}^{m×n}$.
- *Codeword* $y∈\{0,1\}^n$ which satisfies $Hy=0 \mod 2$.
- *Covering radius* 
  $$ρ_H=\max_{x∈\{0,1\}^n}\min_{y∈C_H} d(x,y)$$
  where $d$ is Hamming distance and $C_H$ is the set of all code words.

We define the problem COVERING RADIUS as:

INSTANCE: A parity check matrix $H∈\{0,1\}^{m×n}$ and an integer $r.$

QUESTION: Is the covering radius of the code defined by $H$ at most $r?$

---

We define the language COVERING RADIUS.

$$L = \{H;r ∣ H∈\{0,1\}^{m×n} \text{ such that } ρ_H≤r\}$$

That is, $L$ contains all strings $H;r$ where $H$ is a parity check matrix with a covering radius of at most $r.$

---

The language $L$ is in $Π_2^p$ iff there is a relation $R⊆(Σ^*)^3$ such that

$$L=\{z ∣ ∀x∃y, (x,y,z)∈R\},$$

and whenever $(x,y,z)∈R$ then $|x|,|y|≤|z|^t$ for some $t$.

---

We can write the COVERING RADIUS question in the form, $∀x∃y$ such that $d(x,y)≤r,$ where $x$ and $y$ are binary vectors and $Hy=0$ holds. 

If we represent $x$ and $y$ as strings and set string $z=H;r$, then, have $|x|,|y|≤|z|^t$ for some $t$ whenever $(x,y,z)∈R.$


# H6.3


# References
