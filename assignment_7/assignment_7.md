---
title: "Problem Set 7"
date: \today
author: "Jaan Tollander de Balsch"
bibliography: "bibliography.bib"
csl: "https://raw.githubusercontent.com/citation-style-language/styles/master/harvard-anglia-ruskin-university.csl"
link-citations: true
urlcolor: "blue"
---
# H7.1
Let $L∈𝐙𝐏𝐏=𝐑𝐏∩𝐜𝐨𝐑𝐏.$ Then we have two Monte Carlo Turing machines, $N_1$ which decides $L$ and $N_2$ decides which $\bar{L}.$ We compose PTM $M$ using $N_1$ and $N_2$ such that:

1) If $x∈L$, then $x∉\bar{L}$ and all computations for $N_2$ halt with "yes", thus $Pr[M(x)=0]=0.$

2) If $x∉L$, then all computations for $N_1$ halt with "no", thus $Pr[M(x)=1]=0$

3) Otherwise $Pr[M(x)=?]≤(1/2)^2≤1/3.$

The probability of getting a definite answers in $k$ iterations is atleast $1-2^{-k}$ (polynomial). Consequence from condition (1) is that $M(x)=1$ if and only if $x∈L.$

# H7.2
# H7.3
<!-- # References -->