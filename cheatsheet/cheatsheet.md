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

<!-- O-notation,  Language, example of tape, Deterministic $k$-tape Turing machine, nondeterministic Turing machine, Decidability, acceptability, Halting problem, reduction, Rice's theorem, Complexity classes -->


# Deterministic single-tape Turing machine
A Turing machine is a quadruple $M=(K,Σ,δ,s)$ where

* $K$ is a finite set of **states** and $s∈K$ is a designated **initial state**,
* $Σ$ is a finite set of **symbols** (the **alphabet** of $M$) so that $⊳,⊔∈Σ$
  * $⊳$ is the **start symbol** and
  * $⊔$ is the **blank symbol**,
* $δ$ is the **transition function**: $$K×Σ → (K∪\{h,yes,no\})×Σ×\{→,←,-\}$$ where the **halting state** $h$, the **accepting state** $yes$, and the **rejecting state** $no$ are not in $K$, and the symbols $→$ (right), $←$ (left), and $-$ (stay) indicate **cursor directions** on the input tape.

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

The relation $→^M$ **yields in one step**: $(q,w,u)→^M (q',w',u'),$ where $q',w',u'$ are obtained according to the transition function.

The relation **yields in $k$ steps** $→^{M^k}$.

The relation **yields** $→^{M^*}$.
