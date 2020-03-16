---
title: "Problem Set 8"
date: \today
author: "Jaan Tollander de Balsch"
bibliography: "bibliography.bib"
csl: "https://raw.githubusercontent.com/citation-style-language/styles/master/harvard-anglia-ruskin-university.csl"
link-citations: true
urlcolor: "blue"
---
# H8.1
Zero-knowledge interactive proof system for graph isomorphism problem.

---

*RSA cryptosystem*: Key pair $(p,q,e,d)$, message $x$ and encrypted message $y$.

*Graph isomorphism*: Graphs $G=(V,E)$ and $G'=(V',E')$ are isomorphic if and only if there exists a bijection 
$$χ:V→V'$$
such that for all $(i,j)∈E$ there exists $(χ(i),χ(j))∈E'$.

We say that $χ$ is a *certificate of graph isomorphism*.

---

**Alice** wants to convince **Bob** with high probability that she has certificate of graph isomorphism without revealing any other information about the certificate.

**Alice** and **Bob** know the input $x=(G,G')$ which is a pair of graphs $G=(V,E)$ and $G'=(V',E')$ such that $|V|=|V'|$ and $|E|=|E'|.$

**Alice** claims to have a certificate $χ$ of graph isomorphism of input $x.$

*Protocol*: In each round 

1) **Alice**

     * Creates a random permutation $π:V'→V'$
     * For each vertex $i∈V$: Generate RSA key pair $(p_i,q_i,e_i,d_i)$ and compute $y_i,$ a randomized RSA coding of $π(χ(i))$ and reveals $(e_i,p_iq_i,y_i)$ to Bob.
     * Reveals the permutation of the edges $E'_π=\{(π(i'),π(j'))∣(i',j')∈E'\}$ to Bob. 

     > (I am not sure if this needs to be encrypted as well? Bob might be able to infer knowledge from $E'_π$)

2) **Bob** picks two random vertices $i,j∈V$ and Alice reveals values $d_i,d_j.$

3) **Bob** decodes $y_i,y_j$ to obtain $i'_π=π(χ(i)),j'_π=π(χ(j))$ and checks

    * Bijectivity: If $i≠j$ then $i'_π≠j'_π.$ 
    * Adjacency: If $(i,j)∈E$ then $(i'_π,j'_π)∈E'_π$ otherwise $(i'_π,j'_π)∉E'_π.$

---

**Alice** must send the whole encrypted certificate so that she cannot fake the certificate for vertices $i,j∈V$ after Bob asks for them.

**Bob** must pick the vertices at random so that Alice cannot predict these vertices and fake the certificate for those vertices.

# H8.2


# H8.3


<!-- # References -->