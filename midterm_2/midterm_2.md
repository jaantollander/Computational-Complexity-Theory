---
urlcolor: "blue"
classoption:
- twocolumn
geometry:
- right=1cm
- left=1cm
- top=1.5cm
- bottom=1.5cm
pagestyle: empty
---

<!-- * CNF formula, Graphs, Sets/subsets, Numbers/Matrices -->

# Complexity Classes
**Non-deterministic polynomial time**: $𝐍𝐏$

* $\mathbf{coNP} = \{L ∣ \bar{L}∈𝐍𝐏\}$
* $L∈\mathbf{NP∩coNP}$ is equivalent to $L∈𝐍𝐏$ and $L∈\mathbf{coNP}$

**Polynomial time hierarchy**: $𝐏𝐇=⋃_{k≥0} Σ_{k}^p$

* $Δ_0^p=Σ_0^p=Π_0^p=𝐏$
* $Δ_{k+1}^p=𝐏^{Σ_k^p},\quad k≥0$
* $Σ_{k+1}^p=𝐍𝐏^{Σ_k^p},\quad k≥0$
* $Π_{k+1}^p=\mathbf{coNP}^{Σ_k^p},\quad k≥0$

**Alternating Turing machine**: $𝐀𝐋, 𝐀𝐏$

**Parallel computation**: 

* $𝐍𝐂=𝐏𝐓/𝐖𝐊(\log^k n, n^k)$
* $𝐍𝐂_j=𝐏𝐓/𝐖𝐊(\log^j n, n^k)$
* Efficient: $𝐍𝐂_1, 𝐍𝐂_2$

**Randomised computation**: 

* Monte Carlo: $𝐑𝐏$
* Las Vegas: $𝐙𝐏𝐏=𝐑𝐏∩\mathbf{coRP}$
* Majority: $𝐏𝐏$
* Efficient: $𝐁𝐏𝐏$

**Interactive proofs**: $𝐈𝐏$

**Counting complexity**: $\#𝐏$

**Parameterised complexity**: 

* Fixed-parameter tractable: $\mathbf{FTP}$
* Problems in $𝐗𝐏$ have polynomial-time solutions for every constant value of paramter $k$

**Class inclusions**:

* $𝐋⊆𝐍𝐋⊆𝐏⊆𝐍𝐏⊆𝐏𝐇⊆\mathbf{PSPACE}⊆\mathbf{EPX}$
* $𝐍𝐂_1⊆𝐋⊆𝐍𝐋⊆𝐍𝐂_2⊆𝐍𝐂⊆𝐏$
* $𝐀𝐋=𝐏, 𝐀𝐏=\mathbf{PSPACE}, \mathbf{APSPACE}=\mathbf{EXP}$
* $𝐏⊆𝐙𝐏𝐏⊆𝐑𝐏⊆𝐍𝐏⊆𝐏𝐏$
* $𝐑𝐏⊆𝐁𝐏𝐏⊆𝐏𝐏$
* $𝐍𝐏⊆\#𝐏⊆\mathbf{PSPACE}$
* $𝐏𝐇=𝐏^{\#𝐏}=𝐏^{𝐏𝐏}$ (Toda's theorem)
* $𝐈𝐏=\mathbf{PSPACE}$
* $\mathbf{FTP}⊆𝐗𝐏$


# Logspace
For input of length $n$, the total number of possible configurations for **logspace** decider is $c^{O(\log n)}=n^{O(1)}$ where $c$ is constant. Therefore, $𝐋⊆𝐍𝐋⊆𝐏.$


# NL-completeness
**Reachability**: Given graph $G=(V,E)$ and vertices $s,t∈V$. Is there a path from $s$ to $t$ in $G$?

**Reachability is NL-complete**.

1) **Reachability is in NL**: Start from vertex $s$ and nondeterministically walk to every other reachable vertex. Return $yes/no$ whether vertex $t$ is reached.

2) **Reachability is NL-hard**: Consider the computation state graph of any other **NL** algorithm. Such algorith will accept only if there is nondeterministic path from start to accepting state.

**2SAT is NL-complete**


# Polynomial Time
Ciruit value and hornsat are $𝐏$-complete. They are least likely to be in $𝐍𝐂,$ that is, efficiently solvable by parallel algorithms.


# Oracle Turing Machines
An **oracle Turing machine** $M^?$

* Query string $y$, query state $q^?$, answer states $q_{yes},q_{no}.$
* From the query state $q^?$ the machine moves to $q_{yes}$ or to $q_{no},$ depending on whether $y∈A$ holds or not, where $A$ is the oracle set.
* A query is performed in one step.
* Computation of $M^?$ with oracle $A$ on input $x$ is $M^A(x).$

**Relativised complexity class**: $C^A$ where $C$ is complexity class and $A$ is an oracle.

**Example**: There exists oracle $A$ for which $𝐏^A=𝐍𝐏^A$.

**Proof**: Let $A$ be a $\mathbf{PSPACE}$-complete. Then $\mathbf{PSPACE}⊆𝐏^A⊆𝐍𝐏^A⊆\mathbf{NPSPACE}⊆\mathbf{PSPACE}.$


# Padding
**Padding** $x;1^d$ of string $x.$

**Padding argument**: If $𝐏=𝐍𝐏$ the $\mathbf{EXP}=\mathbf{NEXP}.$

Let $N=c^{n^{O(1)}}$ and $c$ be a constant. Then
$$
\begin{aligned}
NEXP(n) &= NTIME(c^{n^{O(1)}}) = NTIME(N) ⊆ NP(N) \\
&⊆ P(N) = TIME(N^{O(1)}) = TIME(c^{n^{O(1)}}) = EXP(n).
\end{aligned}
$$


# NP
A relation $R⊆Σ^*×Σ^*$ is **polynomially decidable** if there is a deterministic TM deciding the language $\{x;y∣(x,y)∈R\}$ in polynomial time.

A relation $R$ is **polynomially balanced** if $(x,y)∈R$ implies $|y|≤|x|^k$ for some $k≥1.$

**Succint certificate**: Language $L$ is in $𝐍𝐏$ iff there is a polynomially balanced and polynomially decidable relation $R$ such that 

$$L = \{x ∣ (x,y)∈R, ∃y∈Σ^*\}.$$

Language $L$ is $𝐍𝐏$-complete if:

1) $L∈𝐍𝐏$ : $L$ is in $𝐍𝐏.$
2) $L'≤_{\mathrm{L}} L$ : Known $𝐍𝐏$-complete language $L'$ has logspace reduction to $L$.


# Polynomial-time Hierarchy
A relation $R⊆(Σ^*)^{k+1}$ is said to be **polynomially balanced** if whenever $(x,y_1,...,y_k)∈R,$ it holds that $|y_1|,...,|y_k|≤|x|^t$ for some $t.$

---

Language $L$ is in $Σ_k^p$ for $k≥1$ iff there is a polynomially balanced relation $R$ such that the language $\{x;y∣(x,y)∈R\}$ is in $Π_{k-1}^p$ and 

$$L=\{x∣∃y, (x,y)∈R\}.$$

---

Language $L$ is in $Π_k^p$ for $k≥1$ iff there is a polynomially balanced relation $R$ such that the language $\{x;y∣(x,y)∈R\}$ is in $Σ_{k-1}^p$ and 

$$L=\{x∣∀y, (x,y)∈R\}.$$

---

Language $L$ is in $Σ_k^p$ for $k≥1$ iff there is a **polynomially balanced, polynomial-time decidable** $(k+1)$-ary relation $R$ such that

$$L = \{x ∣ ∃y_1 ∀y_2 ∃y_3 ⋯ Qy_k, (x,y_1,...,y_k)∈R\}$$

where $Q$ is $∀$ if $k$ is even and $∃$ if $k$ is odd.

---

Language $L∈𝐏𝐇$ iff $L∈Σ_k^p$ for some $k.$

---

**Example**: $𝐏𝐇⊆\mathbf{PSPACE}$

**Proof**:

* Base case: $Σ_0^p=𝐏⊆\mathbf{PSPACE}$
* Recursive case: $k≥0$
  * Assume: $Σ_k^p⊆\mathbf{PSPACE}$
  * Then: $Σ_{k+1}^p=𝐍𝐏^{Σ_k^p}⊆\mathbf{NPSPACE}⊆\mathbf{PSPACE}$. Last step from Savitch's theorem. Oracle doesn't use additional space, $𝐍𝐏$ takes at most polynomial space.

---

**Quantified satisfiability**: $QSAT_k$: Given a boolean expression $ϕ$ with its variables partitioned into sets $X_1,...,X_k$. Is the following true?

$$∃X_1 ∀X_2 ⋯ QX_k ϕ$$

where $Q$ is $∀$ if $k$ is even and $∃$ if $k$ is odd.

$QSAT_k$ is $Σ_k^p$-complete for all $k≥1.$

---

**Example**: $QSAT_2∈Σ_2^p$ but not in $Σ_1^p=𝐍𝐏$.

In order to verify a certificate for $QSAT_2$, we need to check $2^{|X_2|}$ times boolean formulas of length $|X|$, which means it is not polynomial time verifiable and thus $QSAT_2∉Σ_1^p=𝐍𝐏$ assuming $𝐏≠𝐍𝐏.$

---

* $L∈Σ_2^p=𝐍𝐏^{𝐍𝐏}$ : Covering radius
* $L∈Π_2^p=\mathbf{coNP}^{𝐍𝐏}$ : Integer expression equivalence


# NP-complete problems
$𝐍𝐏$-complete problems

**Boolean problems**: circuit sat, sat, 3SAT, MAX2SAT, NAESAT

**Graph cover and packing problems**: Independent Set, Clique, Vertex Cover, Max Cut, Max Bisection, Bisection Width

**Graph path and coloring problems**: Hamilton Path, Travelling Salesperson (TSP), $k$-coloring

**Set problems**: Exact Cover by 3-Sets, Set Cover, Set Packing

**Number problems**: Integer programming, Knapsack

---

Example reductions:

- circuit sat → sat
- sat → 3-sat
- circuit sat → naesat
- 3-sat → independent set
- independent set → clique
- independent set → vertex cover
- naesat → max cut
- max cut → max bisection
- naesat → 3-coloring
