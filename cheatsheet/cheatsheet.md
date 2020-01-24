---
# title: "Computational Complexity Theory -- Cheatsheet"
# date: \today
# author: "Jaan Tollander de Balsch"
bibliography: "bibliography.bib"
csl: "https://raw.githubusercontent.com/citation-style-language/styles/master/harvard-anglia-ruskin-university.csl"
link-citations: true
urlcolor: "blue"
classoption:
- twocolumn
geometry:
- right=2cm
- left=2cm
- top=2cm
- bottom=2cm
---
<!-- Definitions, notation, examples -->

<!-- O-notation, example of tape, example of transition diagram, Halting problem, reduction, Rice's theorem

Linear speedup: Time and memory
-->


# Deterministic single-tape Turing machine
A Turing machine is a quadruple $M=(K,Σ,δ,s)$ where

* $K$ is a finite set of **states** and $s∈K$ is a designated **initial state**,
* $Σ$ is a finite set of **symbols** (the **alphabet** of $M$) so that $⊳,⊔∈Σ$
  * $⊳$ is the **start symbol** and
  * $⊔$ is the **blank symbol**,
* $δ$ is the **transition function**: 
  $$δ : K×Σ → (K∪\{h,yes,no\})×Σ×\{→,←,-\}$$
  where the **halting state** $h$, the **accepting state** $yes$, and the **rejecting state** $no$ are not in $K$, and the symbols $→$ (right), $←$ (left), and $-$ (stay) indicate **cursor directions** on the input tape.

## Transition functions
For current state $q∈K$ and current symbol $σ∈Σ$, $δ(q,σ)=(p,ρ,D)$ where 

* $p$ is the new state,
* $ρ$ is the symbol to be replacing $σ$, and
* $D∈\{→,←,-\}$ is the direction in which the cursor will move.

It is required that $⊳$ alway directs the cursor to the right and is never erased. Formally, for any states $p$ and $q$ we have $δ(q,⊳)=(p,⊳,→)$.

If the machine moves off the right end of the tape, it reads the black symbol $⊔$. String of the tape can become longer, but not shorter. The blanks $⊔$ keep track of the space used by the machine.

## Starting and Halting
The program starts with 

* initial state $s$,
* the tape contents initialised to $⊳x$ where the **input** $x$ is a finitely long string in $(Σ-\{⊔\})^*$ and
* the cursor pointing to $⊳$.

Machine has **halted** when it has reached one of the halting states $\{h,yes,no\}$. On $yes$, machine **accepts** the input, and on $no$ machine **rejects** the input.

The **output** $M(x)$ is

* If $M$ accepts/rejects, then $M(x)=yes/no$.
* If $M$ reaches state $h$, then $M(x)=y$, where $⊳y⊔⊔...$ is the string on the tape of $M$ at the time of halting.
* If $M$ does not halt, then $M(x)=↗$.

## Operational Semantics
A **configuration** of machine $M$ is a triple $(q,w,u)$, where

* $q∈K$ is the current state,
* $w∈Σ^+$ is the string to the left of the cursor, including the symbol scanned by the cursor, and
* $u∈Σ^*$ is the string to the right of the cursor

The relation $→^M$ **yields in one step** $(q,w,u)→^M (q',w',u'),$ where $q',w',u'$ are obtained according to the transition function.

The relation **yields in $k$ steps** $(q_1,w_1,u_1)→^{M^k}(q_k,w_k,u_k)$ if there exists configurations 
$$
(q_1,w_1,u_1) →^{M} (q_2,w_2,u_2) →^{M} ... →^{M}(q_k,w_k,u_k)
$$

The relation **yields** $(q,w,u)→^{M^*}(q',w',u')$ if there exists some $k≥0$ such that $(q,w,u)→^{M^k}(q',w',u').$

# Decidable and Semidecidable Languages
Let $L⊆(Σ-\{⊔\})^*$ be a **language**.

A Turing machine $M$ **decides** $L$, if for every string $x∈(Σ-\{⊔\})^*$, 

* if $x∈L$, then $M(x)=yes$ and
* if $x∈L$, then $M(x)=no$.

If $L$ is decided by some Turing machine, $L$ is called a **decidable** language.

A Turing machine $M$ **computes** a function $$f:(Σ-\{⊔\})^* → Σ^*,$$ if for every string $x∈(Σ-\{⊔\})^*$, $M(x)=f(x).$ If such an $M$ exists, $f$ is called a **computable** function.

A Turing machine $M$ **accepts** or **semidecides** $L$, if for every string $x∈(Σ-\{⊔\})^*$, 

* if $x∈L$, then $M(x)=yes$ and
* if $x∈L$, then $M(x)=↗$.

If $L$ is accepted by some Turing machine, $L$ is called a **semidecidable** language.


## Deterministic $k$-tape Turing machine
A **$k$-tape Turing machine**, for some integer $k≥1,$ is a quadruple $M=(K,Σ,δ,s)$ where the transition function is generalized to handle $k$-tapes simultaneously
$$
δ : K×Σ → (K∪\{h,yes,no\})×(Σ×\{→,←,-\})^k.
$$

Transitions for $k$-tape machines are of the form
$$
δ(q,σ_1,...,σ_2) = (p,ρ_1,D_1,...,ρ_k,D_k).
$$

A **configuration** is defined as a $2k+1$-tuple
$$
(q,w_1,u_1,...,w_k,u_k).
$$

A $k$-tape machine with input $x$ starts from the configuration
$$
(s,⊳,x,⊳,ϵ,...,⊳,ϵ),
$$
where $ϵ$ is the empty string.

**Output** is defined as for standard machines

* if $(s,⊳,x,⊳,ϵ,...,⊳,ϵ)→^{M^*} (h,w_1,u_1,...,w_k,u_k)$, then $M(x)=y$ where $y$ is $w_k u_k$ with the leading $⊳$ and trailing $⊔$s removed, that is, output is read from the last ($k$th)tape.

The **runtime** of $M$ on input $x$ is $t$ if 
$$(s,⊳,x,⊳,ϵ,...,⊳,ϵ)→^{M^t} (H,w_1,u_1,...,w_k,u_k),$$
where $H∈\{h,yes,no\}$. If $M(x)=↗$, then the runtime is considered to be $∞.$


# Time Complexity
Machine $M$ **operates within time** $f(n),$ if for any input string $x,$ the runtime by $M$ on $x$ is at most $f(|x|)$ where $|x|$ is the size of the input $x.$ 

Also, $f(n)$ is **(upper) time bound** for $M$ and the language $L$ decided by $M$ belongs to the **time complexity class** $\mathbf{TIME}(f(n)).$

The set of all languages decidable by deterministic Turing machines in polynomial time is defined as:
$$
𝐏 = ⋃_{k>0} \mathbf{TIME}(n^k).
$$

# Space Complexity
A $k$-tape Turing machine $k>2$ **with input and output** is an ordinary $k$-tape Turing machine with the following restrictions on the transitions function $δ$: 

If $δ(q,σ_1,...,σ_k)=(p,ρ_1,D_1,...,ρ_k,D_k),$ then

1) $ρ_1=σ_1$ (read-only input string)
2) $D_k≠←$ (write-only output string), and
3) if $σ_1=⊔,$ then $D_1=←$ (end of input respected).


## Space Usage
Suppose for a $k$-tape Turing machine $M$ and an input $x$ we have
$$(s,⊳,x,⊳,ϵ,...,⊳,ϵ)→^{M^*} (H,w_1,u_1,...,w_k,u_k),$$
where $H∈\{h,yes,no\}$ is Halting state. Then, the **space used** is
$$∑_{i=1}^k|w_i u_i|$$

If $M$ is a Turing machine *with input and output*, the space used is
$$∑_{i=2}^{k-1}|w_i u_i|$$
We exclude the effect of reading the input and writing the output as regards TM space usage.

Let $f:ℕ→ℝ^+$. Turing machine $M$ **operates within space** $f(n)$ if for any input $x$, $M$ uses space at most $f(|x|).$

## Space Complexity Classes
The **space complexity class** $\mathbf{SPACE}(f(n))$ comprises the family of languages $L$ that can be decided by Turing machines with input and output operating within space $f(n).$

The class $\mathbf{SPACE}(log(n))$ is denoted by $𝐋.$


# Nondeterministic Turing Machines
A nondeterministic Turing machine (NTM) is a quadruple $N=(K,Σ,Δ,s)$ where $Δ$ is a **transition relation**:
$$
Δ⊆(K × Σ) × [(K∪\{h,yes,no\})×Σ×\{→,←,-\}]
$$

Yields is a relation $(q,w,u)⊢_N(q',w',u')$ if there exists a tuple in $Δ$ that makes this a legal transition.

A nondeterministic Turing machine $N$ **decides** a language $L$ if for any $x∈Σ^*,$ the following holds

1) all the computation sequences of $N$ on input $x$ halt, and
2) $x∈L$ iff at least one of them ends in state $yes$
