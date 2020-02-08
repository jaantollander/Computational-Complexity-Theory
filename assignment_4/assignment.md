---
title: "Problem Set 4"
date: \today
author: "Jaan Tollander de Balsch"
bibliography: "bibliography.bib"
csl: "https://raw.githubusercontent.com/citation-style-language/styles/master/harvard-anglia-ruskin-university.csl"
link-citations: true
urlcolor: "blue"
---
# H4.1
## (a)
The problem is in $𝐍𝐏$ because the problem is a special case on SAT which is in $𝐍𝐏$. Next, we will show that the problem is $𝐍𝐏$-complete by reducing SAT to this problem in log space. For this reduction, we use the idea by @79218.

---

Let $ϕ$ be a SAT formula in CNF form. Then, new formula $ϕ'$ in CNF that is logically equivalent to $ϕ$ is constructed as follows.

Add all clauses $c$ in $ϕ$ that have $1$ or $2$ literals to $ϕ'$ unmodified.

For all clauses $c$ in $ϕ$ with more than $3$ literals

1) Create new clause $c'$ by substituting each negative literal $¬x$ in clause $c$ by new variable $z.$
2) Add clauses $c'$, $(x∨z)$ and $(¬x∨¬z)$ to the formula $ϕ'$.

---

Proof: Literal $z$ is forced to act as literal $¬x$ because
$$
z ∧ (x∨z) ∧ (¬x∨¬z)
$$
is true only if $z$ and $¬x$ are true, which is evident from its truth table.


## (b)
1-IN-3SAT is in $𝐍𝐏$ since verifying the correct solution is same as for normal SAT. We show $𝐍𝐏$-completeness by reducing 3SAT to 1-IN-3SAT.

---

logical equivalence, force exactly one literal in each clause to be true


# H4.2
## (i)


## (ii)


# H4.3
## (i)


## (ii)



<!-- # References -->