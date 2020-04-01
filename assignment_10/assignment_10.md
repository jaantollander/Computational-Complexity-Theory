---
title: "Problem Set 10"
date: \today
author: "Jaan Tollander de Balsch"
bibliography: "bibliography.bib"
csl: "https://raw.githubusercontent.com/citation-style-language/styles/master/harvard-anglia-ruskin-university.csl"
link-citations: true
urlcolor: "blue"
---
# H10.1
**Vertex Cover**

* **Instance**: An undirected graph $G=(V,E)$ and an integer $B.$
* **Question**: Is there a subset $C⊆V$ with $|C|≤B$ such that for every $(i,j)∈E,$ either $i∈C$ or $j∈C$?

*Given a graph, is there a set of vertices of size at most given threshold such each edge has atleast one end point in the set?*

---

**Directed Cycle Cover**

* **Instance**: A directed graph $G=(V,E)$ and an integer $K.$
* **Question**: Is there a subset $F⊆E$ with $|F|≤K$ such that any directed cycle in the graph $G$ contains at least one arc (directed edge) from set $F$?

*Given a directed graph, is there a set of arcs of size at most given threshold that need to be removed to make it acyclic?*

---

Directed Cycle Cover is in **NP**. We can check the certificate in polynomial time as follows. 

**Proof**: Given a directed graph $G=(V,E)$ and subset $F⊆E$ with $|F|≤K,$ check if graph $G'=(V,E∖F)$ is acyclic using depth first search which runs in polynomial time $O(|V|+|E∖F|)=O(|V|+|E|)$.

---

We show that Directed Cycle Cover is **NP**-hard by logspace reduction from Vertex Cover.

1) Let the undirected graph $G=(V,E)$ and integer $B$ be an instance of vertex cover.

FIXME: solution is not correct

2) Then, we transform it into an instance of directed cycle cover $G'=(V,E')$ where for each edge $(i,j)∈E$, there we create a cycle by creating arcs $(i,j)∈E'$ and $(j,i)∈E'.$ The tranformation can be computed in logspace.
3) Since the arcs form a cycle, Directed Cycle Cover is forced to choose one of them. 
4) Let $F⊆E'$ with $|F|≤B$ be a solution for directed cycle cover. Then, the solution for vertex cover is $C=\{i∣(i,j)∈F\}$ with $|C|≤B.$

**Proof**: $F$ is directed cycle cover $⇔$ $C$ is vertex cover

$⇒$:

$⇐$:

# H10.2
# H10.3
<!-- # References -->