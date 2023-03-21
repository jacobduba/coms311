# Lecture 3-20

The **adjacency-list representation** of a graph $G = (V, E)$ consists of an array $Adj$, of $|V|$ lists, one for each vertex in $V$.
For each $u \in V$, the adjacent list $Adj[u]$ contains all the vertices adjacent to $u$ in $G$.
In the adjacency matrix representation of a graph $G = (V,E)$

## Cycles

A cycle in a graph is a path of length at least 4 in which only the first and last vertices are equal.
A cycle of length $3$ in the graph.

## Trees

A tree is a connected graph with no cycles.
The number of edges in a tree with $n$ vertices is $n - 1$.

## Breadth-First Search
**Breadth-First Search** (BFS) is a simple search algorithm for answering basic questions about a graph.
Below are some useful applications of this algorithm.

* BFS computers the distance from a source vertex to each reachable vertex, where the distance between two vertices in an unweighted graph is the smallest number of edges in any path between the vertices.
* BFS can be used to detect a cycle in the graph.
* We can use BFS to check where a path exists between two vertices.
* We can use BFS to find all the vertices within a connected component of a graph.
* BFS can be used to check if a graph is bipartite. A bipartite graph can be decomposed into two disjoint sets such that no two vertices within the same set are adjacent.

```
BFS(G,s)
    for each vertex in u in G.V - {s}
        u.color = WHITE
        u.d = INFINITY
        u.pi = NIL
    s.color = GRAY
    s.d = 0
    s.pi = NIL
    Q = empty queue
    ENQUEUE(Q,s)
    while (Q != empty)
        u = DEQUEUE(Q)
        for each v in G.Adj[u]
            if v.color == WHITE
                v.color = GRAY
                v.d = u.d + 1
                v.pi = u
                ENQUEUE(Q,v)
        u.color = BLACK
```

## Shortest Paths

Let $s$ be a given vertex in a graph $G = (V,E)$.

The **shortest-path distance** $\delta(s,v)$ is defined as the minimum number of edges in any path from vertex $s$ to vertex $v$; if there is no path from $s$ to $v$, then $\delta(s,v) = \infty$.

To show that BFS correctly computers the shortest path distances, you will need to show that the following two properties hold:

### Proof

1.  
    If $u$ is reachable from $s$, then so is $v$.

    In this case, $\delta(s,u) + 1$ is the length of the shortest path $s$ to $u$ and then $v$ via the edge $(u,v)$.

    $S(S, v) is the length of the shortest path from $s$ to $v$.
Thus, the inequality $\delta(s,u) + 1 \leq \delta(s,v)$ holds.

    If $u$ is not reachable from $s$, then $S(s, u) = \infty$ and the inequality holds.

2.
    We use the induction on the number of `ENQUEUE` operations to show that $v.d \geq \delta(s,v)$.
    Note that if v is never enqueued then v is not reachable from s and $v.d = \infty \geq \delta(s,v)$.

    Consider the basis of induction...

    From the assignment in lines 15 and from Lemma 22.1, we have $v.d = u.d + 1 \geq \delta(s,v)$

    Note that vertex v is never enqueued again because it grayed and lines 14-17 are executed only for white vertices.
    Thus, the value of $v.d$ never changes again.
