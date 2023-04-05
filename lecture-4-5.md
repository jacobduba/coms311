# Lecture 4-5

## The Workings of the GENERIC MST Algorithm Method

During the execution of the method, the set $A$ is always acyclic, otherwise a minimum spanning tree containing all the edges of $A$ world contain a cycle, a contradiction.

(The loop invariant says that the set $A$ is a subset of a minimum spanning tree.)

At any point in the execution, the graph $G_A = (V,A)$ is a forest, where each of the connected components of $G_A$ is a tree.

For example, at the beginning of the method, $A$ is empty, and the forest contains $|V|$ trees, one for each vertex.

Moreover, any safe edge $(u,v)$ for $A$ connects distinct components of $G_A$ since $A \cup \{(u,v)\}$ must be acyclic.

The number of iterations for the **while** loop in lines 2-4 of the method $|V| - 1$, because each iteration finds one of the

## Corollary 23.2

Let $G = (V, E)$ be a connected, undirected graph with a real-valued weight function $w$ defined on $E$.

Let $A$ be a subset of $E$ that is included in some minimum spanning tree for $G$, and let $C = (V_C, E_C)$ be a connected component (tree) in the forest $G_A = (V, A)$.

If (u, v) is a light edge connecting $C$ to some other component in $G_A$, then $(u, v)$ is safe for $A$.

## Proof

The cut $(V_C, V - V_C)$ respects $A$, and $(u, v)$ is a light edge for this cut.
Thus, $(u, v)$ is safe for $A$.

## Prim's Algorithm

Prim's algorithm, a variation of Dijkstra's algorithm, finds a minimum spanning tree.

In Prim's Algorithm, the edges in the set $A$ always form a single tree.

The tree starts from an arbitrary root vertex $r$ and grows until the tree includes all the vertices in $V$.

The algorithm repeatedly selects an edge of the least weight connecting $A$ to a new vertex on which no edge of $A$ is incident, and adds the edges to $A$.

Thus, this rule adds only safe edges to $A$; so when the algorithm terminates, the edges in $A$ form a minimum spanning tree.

## Implementation of Prim's Algorithm

The algorithm keeps all vertices that are not in the tree in a min-priority queue $Q$ based on a key attribute.

For each vertex $v$, the attribute v.key is the minimum weight of any edge connecting v to a vertex in tree.

If there is no such edge...
...
...

```
MST-PRIM(G, w, r)
    for each vertex u in G.V
        u.key = ∞
        u.π = NIL
    r.key = 0
    Q = G.V # Q is a minheap
    while Q is not empty
        u = EXTRACT-MIN(Q)
        for each vertex v in G.Adj[u]
            if v ∈ Q and w(u, v) < v.key
                v.π = u
                v.key = w(u, v)
```

## Loop Invariant

At the start of each iteration of the **while** loop, the loop invariant consists of three parts:

1. $A = \{(v, v.π) : v ∈ V - \{r\} - Q\}$ is a minimum spanning tree for $G$.

...

Line 7 selects a vertex $u \in Q$ incident on a light edge crossing the cut $(V - Q, Q)$ except iteration 1.

Removing $u$ from the set $Q$ is equivalent to adding it to the set $V - Q$, and adding $(u, u.π)$.

The **for** loop on lines 8-11 updates the key and pi attributes of every vertex v adjacent to u but not in the tree, maintaining part 3 of the loop invariant.