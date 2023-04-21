# Lecture 4-21

## The Vertex-Cover Problem

A **vertex cover** of an undirected graph $G = (V,E)$ is a subset of $V' \subseteq V$ such that if $(u,v) \in E$, then $u \in V'$ or $v \in V'$.

Thus, a vertex cover for G is a set of vertices that covers all the edges in $E$.

The **size** of a vertex cover is the number of vertices in it.

The **vertex-cover** problem is to find a vertex cover of a minimum size in a given graph.

A decision of this problem is to determin...

We Show that `VERTEX-COVER` is in NP.

We design a polynomial-time algorithm for verifying whether a given graph $G = (V,E)$ contains a vertex cover of size $k$.

A certificate to the algorithm is a subset $V'$ of $V$.

The algorithm confirms that $V'$ is of size $k$ and checks, for each edge $(u,v)$ in $E$, that $u \in V'$ or $v \in V'$.

If so, the algorithm reports 1. Else reports 0...

## The Vertex-Cover Problem is NP-Hard

Next, we show that `CLIQUE \leq_p VERTEX-COVER`.

This reduction depends on the notion of the 'complement' of a graph.

The complement of a graph $G = (V, E)$ is defined as $\bar{G} = <V, \bar{E}>$, where $\bar{E} = \{(u,v) : u, v \in V,$ and $(u,v) \notin E\}$.

In other words, $\bar{G}$ is the graph containing exactly those edges that are not in $G$.

Our reduction algorithm transforms an instance $<G, k>$ of the clique problem into an instance $<\bar{G}, |V| - k>$ such that $G$ contains a clique of size $k$ if and only if $\bar{G}$ contains a vertex cover of size $|V| - k$.

Assume that $G$ contains a clique $V'$ of size $k$, $V' \subseteq V$.

We show that $\bar{G}$ contains a vertex cover $V - V'$.

Consider an edge $(u,v) \in \bar{E}$. By the definition of $\bar{E}$, we have $(u,v) \notin E$.

Because each pair of vertices in $V'$ is connected by an edge of $E$, the fact that $(u,v) \not in E$, means that at least one of $u$ or $v$ is not in $V'$.

Conversely, assume that $\bar{G}$ contains a vertex cover $V' \subseteq V$, where $|V'| = |V| - k$.

Then, for all $u$, $v \in V$, if $(u,v) \in \bar{E}$, then we have $u \in V'$ or $v \in V'$.

The contrapositive of this implication is that for all $u$, $v \in V$, if $u \notin V'$ and $v \notin V'$, then $(u,v) \in \bar{E}$.

Equivalently, for all $u$, $v \in V$, if $u \in V - V'$ and $v \in V - V'$, then $(u,v) \in E$. So $V - V'$ is a clique of size $|V| - |V'| = k$.