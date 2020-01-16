---
title: "Problem Set 1"
date: \today
author: "Jaan Tollander de Balsch"
bibliography: "bibliography.bib"
csl: "https://raw.githubusercontent.com/citation-style-language/styles/master/harvard-anglia-ruskin-university.csl"
link-citations: true
urlcolor: "blue"
---
@papa1994, chapters: 1, 2.1-2.5

# H1.1
## i)
We say that $g(n)$ dominates $f(n)$ if 
$$
\lim_{n→∞} \frac{f(n)}{g(n)} → 0.
$$

---

Let prove $(\log_2 n)^s=O(n^r)$ for $s,r>1$, that is $n^r$ dominates $(\log_2 n)^s$.

$$
\lim_{n→∞} \frac{(\log_2 n)^s}{n^r} = \left(\lim_{n→∞} \frac{\log_2 n}{n^{r/s}}\right)^s
$$
Using L'hopital's rule
$$
\left(\lim_{n→∞} \frac{1}{(r/s) n^{r/s} \log (2)}\right)^s → 0
$$

From the above limit, we see that $n^r≠O((\log_2 n)^s)$, since $n^r$ dominates $(\log_2 n)^s.$


## ii)
Upper bound
$$
\begin{aligned}
\log_2 n! &= ∑_{i=1}^n \log_2 i \\
& ≤ ∑_{i=1}^n \log_2 n \\
& = n \log_2 n.
\end{aligned}
$$
All the terms $\log_2 i$ are smaller or equal to $\log_2 n$.

Lower bound (assuming even $n$)
$$
\begin{aligned}
\log_2 n! &= ∑_{i=1}^n \log_2 i \\
&= ∑_{i=1}^{n/2} \log_2 i + ∑_{i=n/2}^n \log_2 i \\
&≥ (n/2) \log_2 (n/2) \\
&= (n/2) (\log_2 n - 1).
\end{aligned}
$$
Half of the terms $\log_2 i$ are larger of equal to $\log_2 (n/2)$.

Therefore, the tight bound is
$$
\log_2 n! = ∑_{i=1}^n \log_2 i = Θ(n \log_2 n).
$$

# H1.2
We define our Turing machine as $M=(K,Σ,δ,s)$ where the set of states is $K=\{s,q_1,q_2,q_3,q_4\}$, the set of symbols is $Σ=\{1,⊔,⊳\}$ and the following transition function $δ$:

$p∈K$ | $σ∈Σ$ | $δ(p,σ)$ | Explanation
------|-------|--------- | -----------
$s$ | $1$ | $(q_1,1,→)$ | Move head to next 1
$s$ | $⊔$ | $(h,1,→)$ | Add 1 and halt
$s$ | $⊳$ | $(s,⊳,→)$
$q_1$ | $1$ | $(q_2,1,→)$ | Move head to next one
$q_1$ | $⊔$ | $(h,1,→)$ | Add 1 and halt
$q_2$ | $1$ | $(q_2,1,→)$ | Move cursor to the end of the string of 1's
$q_2$ | $⊔$ | $(q_3,⊔,←)$ | Reached end of the string
$q_3$ | $1$ | $(q_2,⊔,←)$ | Remove first 1
$q_4$ | $1$ | $(h,⊔,←)$ | Remove second 1 and halt

Unreachable states are left out for simplicity.

The execution of the Turing machine for $f(ϵ)$

$$
s,⊳\underline{⊔} → h,⊳1\underline{⊔}
$$

The execution of the Turing machine for $f(11)$

$$
\begin{aligned}
& s,⊳\underline{1}1⊔ → \\
& q_1,⊳1\underline{1}⊔ → \\
& q_2,⊳11\underline{⊔} → \\
& q_3,⊳1\underline{1}⊔ → \\
& q_4,⊳\underline{1}⊔⊔ → \\
& h,\underline{⊳}⊔⊔⊔ 
\end{aligned}
$$

# H1.3
We define a binary alphabet $Σ=\{0,1\}.$

## i)
If language $L⊆Σ^*$ is decidable by a Turing machine $M$ then 

* If $x∈L$, $M(x)=yes$ and
* If $x∉L$, $M(x)=no$

Then, the complement $\bar{L} = Σ^*∖L = \{x∈Σ^*∣x∉L\}$ is decidable by a Turing machine $M'$

* If $x∈\bar{L}$, $M'(x)=yes$ and
* If $x∉\bar{L}$, $M'(x)=no$

By definition we have

* $x∈\bar{L}$ implies $x∉L$ and $M(x)=no$
* $x∉\bar{L}$ implies $x∈L$ and $M(x)=yes$

Turing machine $M'$ decides $yes$ when $M$ decides $no$ and vice versa.

---

If Turing machine $M$ accepts $L$ if for every string $x∈{Σ-\{⊔\}}^*$

* If $x∈L$ then $M(x)=yes$ 
* But, if $x∉L$, $M(x)=↗$.

The complement language $\bar{L}$ is not accepted by a Turing machine $M'$, because if $x∉L$ which implies $x∈\bar{L}$ and $M(x)=↗$. Therefore, Turing machine $M$ may not halt on this input, which implies that Turing machine $M'$ may also not halt.


## ii)
If $L$ is semidecidable it implies $x∈L$, then $M_1(x)=yes$. 

If $\bar{L}$ is semidecidable it implies $x∈\bar{L}$, then $M_2(x)=yes$. 

Since $x∈\bar{L}$ implies $x∉L$, all inputs $x∈L$ and $x∉L$ are decided by some Turing machine, therefore, $L$ is decidable.

# References
