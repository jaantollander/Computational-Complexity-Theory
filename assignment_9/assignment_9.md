---
title: "Problem Set 9"
date: \today
author: "Jaan Tollander de Balsch"
bibliography: "bibliography.bib"
csl: "https://raw.githubusercontent.com/citation-style-language/styles/master/harvard-anglia-ruskin-university.csl"
link-citations: true
urlcolor: "blue"
---
# H9.1
Let $ϕ$ be CNF formula with $m$ clauses. We can formulate a greedy algorithm for deterministic $2$-approximation for MAX SAT..

---

**Create sorted formula $ϕ'.$**

1) Count the amount of each literal in $ϕ.$
2) Sort literals in each clause from most frequent to the least frequent, that is, in decreasing order.
3) Lexicographically sort clauses in decreasing order.

**Greedily assign truth values to the variables**:

For all clauses in $ϕ'$ or until all variables have been assigned a truth value

1) If clause is *satisfied* or *unsatisfied* move to the next clause.
2) If clause is *undetermined*, find the first literal with unassigned variable. Then assign a truth value for the variable such that the clause satisfied.

---

The sorting is required, otherwise given formula 
$$l_1 ∧ l_2$$
we can build a worse case by adding clauses 
$$¬l_1 ∧ ¬l_2 ∧ (¬l_1∨¬l_2).$$

The greedy assignment would be $l_1=l_2=T$, then $¬l_1=¬l_2=(¬l_1∨¬l_2)=F$, thus the formula would not be $2$-approximation.

**Proof**: Since the literals and clauses are sorted in decreasing order, we can only add two of the three clauses, otherwise the clauses would remain sorted. Therefore, the solution is $2$-approximation in the worst case.

# H9.2

# H9.3

<!-- # References -->