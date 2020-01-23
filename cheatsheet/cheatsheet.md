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

<!-- O-notation, Language, example of tape, example of transition diagram, Deterministic $k$-tape Turing machine, nondeterministic Turing machine, Decidability, acceptability, Halting problem, reduction, Rice's theorem, Complexity classes -->


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
