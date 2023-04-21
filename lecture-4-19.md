# Lecture 4-19

NP-complete problems arise in diverse domains: boolean logic, graph theory, biology, chemistry, physics, and many other areas.

We will use the reduction methodology to show that several problems in graph theory are NP-complete.

Boolean formulas and graphs are powerful systems for expressing various types of computation and relationship.

## The Clique Problem

A **clique** in an undirected graph G = (V, E) is a complete subgraph G' = (V', E'), with $V' \subseteq V$ and $E' \subseteq E$.

CLIQUE = {<G, k> : G is a graph containing a clique of size k}

## The Clique Problem is in NP

We show that CLIQUE is in NP.

We design a polynomial-time for verifying whether a given graph G = (V, E) contains a clique of size $k$.

A certificate to the algorithm is a k-vertex subset of V' of V.

...

## The Clique Problem is NP-Hard

Next, we show that 3-CNF SAT $\leq_p$ CLIQUE.

Let $\theta = C_1 \land C_2 \land \cdots \land C_n$ be a 3-CNF formula with k clauses, an instance of `3-CNF SAT`.

Our reduction algorithm transforms $\theta$ into a graph G = (V, E) and an integer k...

## The Clique Problem is NP-Hard

For example, consider a boolean formula with three clauses in 3-CNF:

$\theta = (x_1 \lor x_2 \lor x_3) \land (x_1 \lor x_2 \lor x_4) \land (x_1 \lor x_3 \lor x_4)$

The vertex set V contains 3 triples of ...

...

Thus, each clause in $\theta$ contains a literal $t^r_i$ that corresponds to a vertex $v^r_i$ in V'.

Because G contains no edges between inconsistent literals, we can assign 1 to each such literal $t^r_i$.

Under this assignment, each clause is satisfied, and $\theta$ is satisfied.