---
urlcolor: "blue"
classoption:
- twocolumn
geometry:
- right=2cm
- left=2cm
- top=2cm
- bottom=2cm
---

<!-- O-notation -->

<!-- k-tape Turing machine -->

<!-- nondeterministic Turing machine -->

**Turing machine**: $M=(K,Σ,δ,s)$, states $K$, symbols $Σ$, transition function $δ$, starting state $s$, starting symbol  $⊳$, blank symbol $⊔$, halting states $\{h,yes,no\}$

**Transition function**: $δ(q,σ)=(p,ρ,D)$, current state $q$, current symbol $σ$, new state $p$, replacing symbol $ρ$, cursor direction $D∈\{→,←,-\}$

**Configuration**: $(q,w,u)$, current state $q$, string left of cursor including scanned symbol $w$, string right of cursor $u$, relations $→^M,→^{M^k},→^{M^*}$

**Language**: $L⊆(Σ-\{⊔\})^*$, complement $\bar{L}=Σ^*-L$

**Decidable/Recursive** $∀x∈(Σ-\{⊔\})^*$: If $x∈L$, then $M(x)=yes$ and if $x∉L$, then $M(x)=no$

**Semidecidable/Accepts** $∀x∈(Σ-\{⊔\})^*$: If $x∈L$, then $M(x)=yes$ and if $x∉L$, then $M(x)=↗$

**Universal Turing machine**: $U(M;x)=M(x)$, simulates machine $M$ on input $x$

**Halting problem**: Does $M$ halt on $x$? Language $H=\{M;x ∣ M(x)≠↗\}$ is semidecidable and undecidable (All $M;x$ where $M$ halts).

TODO: **Undecidability**: Reduce $H$ to $A$ ...

---

**Complexity class**: $C$ is set of all languages decided by Turing machine $M$ operating in appropriate mode such that $M$ expends at most $f(|x|)$ units of specified resource for any input $x$

**Complexity classes**: $\mathbf{TIME}(f)$, $\mathbf{SPACE}(f)$, $\mathbf{NTIME}(f)$, $\mathbf{NSPACE}(f)$, $f$ is proper complexity function

**Closure under complement**: Deterministic time and space classes are closed under complement, if $L∈C$, then $\bar{L}∈C$

**Class inclusion**: $𝐋⊆𝐍𝐋⊆𝐏⊆𝐍𝐏⊆\mathbf{PSPACE}⊆\mathbf{EXP}$

---

**Reduction** $A≤B$: Language $A$ is reducible to language $B$

**Logspace reduction**: 
