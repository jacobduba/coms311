# Lecture 4-3

## Minimum Spanning Trees

A weighted graph is a connected, undirected graph with edge costs.

We want to find an acyclic subset T of edges that connects all the vertices and whose total weight is minimized, where the total eight of *T, w(T)*, is the sum of the costs of all edges in T; $w(T) = \sum_{(u,v) \in T} w(u,v)$.

As *T* is acyclic and connects all the vertices, *T* must be a tree, which is called a spanning tree.

A minimum spanning tree is a spanning tree in which the sum of all the costs is no greater than the sum.

## Applications

Finding a minimum spanning tree is an important problem.

Algorithms for finding a minimum spanning tree have applications in the design of networks such as computer networks, transportation networks, water supply networks, and electrical grids.

They are also used as subroutines in algorithms for other problems such as the traveling salesperson problem.

It can be computed by negating weights for each edge and applying an algorithm for finding a minimum spanning tree.

## Growing a Minimum Spanning Tree

We introduce a generic minimum-spanning-tree method that builds a spanning tree by adding one edge at a time.

This method is later implemented by algorithms named Kruskal's algorithm and Prim's algorithm.

The generic method uses a greedy strategy to grow the minimum spanning tree one edge at a time.

The method keeps a set $A$ of edges with the following loop invariant:

Before each iteration, $A$ is a subset of some minimum spanning tree.

At each step, we select and add an edge (u,v) to $A$ so that $A \cup (u,v)$

## Code

```

```

## Using the Loop Invariant

**Initialization**: After line 1, the set A trivially satisfies the loop invariant.

**Maintenance**:

**Termination**:

## How to Find Safe Edges

Below we discuss how to find safe edges.

## Definitions

A *cut* (S, V - S) of an undirected graph $G = (V, E)$ is a partition of the vertex set V into two nonempty subsets S and V - S.

## Rule for Finding Safe Edges

**Theorem 23.1**: Let $G = (V, E)$ be a connected, undirected graph with a real-value weight function $w$ defined on $E$.
Assume that a subset A of E is included in some minimum spanning tree T for G and that a cut (S, V - S) of G respects A. 
If (u,v) is a light edge crossing
