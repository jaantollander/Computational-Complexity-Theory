---
urlcolor: "blue"
classoption:
- twocolumn
geometry:
- right=1.5cm
- left=1.5cm
- top=1.5cm
- bottom=1.5cm
pagestyle: empty
---

**O-notation**: $f(n)=O(g(n))$, $f$ grows at most as fast as $g,$ if there exists $c>0$ and $n_0>0$ such that for all $n≥n_0,f(n)≤c⋅g(n)$

---

**Turing machine**: $M=(K,Σ,δ,s)$, states $K$, symbols $Σ$, transition function $δ$, starting state $s$, starting symbol  $⊳$, blank symbol $⊔$, halting states $\{h,yes,no\}$

**Transition function**: $δ(q,σ)=(p,ρ,D)$, current state $q$, current symbol $σ$, new state $p$, replacing symbol $ρ$, cursor direction $D∈\{→,←,-\}$

**Configuration**: $(q,w,u)$, current state $q$, string left of cursor including scanned symbol $w$, string right of cursor $u$, relations $→^M,→^{M^t},→^{M^*}$

---

**$k$-tape Turing machine**: $M=(K,Σ,δ,s)$

**Transition function**: $δ(q,σ_1,...,σ_2) = (p,ρ_1,D_1,...,ρ_k,D_k)$

**Configuration**: $(q,w_1,u_1,...,w_k,u_k)$

**With input and output**: First tape is read-only and last tape is write only.

**Runtime** is $t$ if $(s,⊳,x,⊳,ϵ,...,⊳,ϵ)→^{M^t} (H,w_1,u_1,...,w_k,u_k),$ where $x$ is the input and $H∈\{h,yes,no\}.$ 

**Space usage**: $∑_{i=2}^{k-1} |w_i u_i|$ where $|w_i u_i|$ is the length of the concatenation of strings $w_i$ and $u_i.$

TODO: linear speedup

---

TODO: nondeterministic Turing machine

---

**Language**: $L⊆(Σ-\{⊔\})^*$, complement $\bar{L}=Σ^*-L$

**Decidable/Recursive** $∀x∈(Σ-\{⊔\})^*$: If $x∈L$, then $M(x)=yes$ and if $x∉L$, then $M(x)=no$

**Semidecidable/Accepts** $∀x∈(Σ-\{⊔\})^*$: If $x∈L$, then $M(x)=yes$ and if $x∉L$, then $M(x)=↗$

**Universal Turing machine**: $U(M;x)=M(x)$, simulates machine $M$ on input $x$

**Halting problem**: Does $M$ halt on $x$? Language $H=\{M;x ∣ M(x)≠↗\}$ is semidecidable and undecidable (All $M;x$ where $M$ halts on $x$).

**Undecidability**: TODO: Reduce $H$ to $A$ ...

TODO: proof of halting is undecidable

---

**Complexity class**: $C$ is set of all languages decided by Turing machine $M$ operating in appropriate mode such that $M$ expends at most $f(|x|)$ units of specified resource for any input $x$

**Complexity classes**: $\mathbf{TIME}(f)$, $\mathbf{SPACE}(f)$, $\mathbf{NTIME}(f)$, $\mathbf{NSPACE}(f)$, $f$ is proper complexity function

**Closure under complement**: Deterministic time and space classes are closed under complement, that is, if $L∈C$, then $\bar{L}∈C$

**Class inclusion**: $𝐋⊆𝐍𝐋⊆𝐏⊆𝐍𝐏⊆\mathbf{PSPACE}⊆\mathbf{EXP}$

---

**Reduction** $A≤B$: Language $A$ is reducible to language $B$. $A$ is at most as hard as $B.$ Algorithm $R$ that transforms any instance $x$ of $A$ to *equivalent* instance $R(x)$ of $B.$

**Logspace reduction** $A≤_\mathrm{L} B$: Algorithm $R$ is computable by deterministic Turing machine in $O(\log n)$ space.

**$C$-hard**: For every $L'∈C$ is we have $L'≤_\mathrm{L}L.$

**$C$-complete**: If $L∈C$ then for every $L'∈C$ we have $L'≤_\mathrm{L}L.$

$C$ is **closed under reductions** if $L'≤_\mathrm{L}L$ and $L∈C,$ then $L'∈C$

---

TODO: circuit value, cicuit sat, sat, ...
