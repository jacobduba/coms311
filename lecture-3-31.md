# Lecture 3-31

## Corollay 22.8

Vertex v is a proper descendant of vertex u in the depth-first forest for a (directed or undirected) graph G if and only if u.d < v.d < v.f < u.f

### Proof

It follows Theorem 22.7

## Theorem 22.9 (White Path Theorem)

In a depth-first forest of a (directed or undirected) graph, $G = (V, E)$, vertex v is a descendant of vertex u if and only if at the time $u.d$ that $u$ is discovered, there is a path from $u$ to $v$ consisting entirely of white vertices.

### Proof

Assume that v is a descendant of vertex u. If $v = u$, then the path from $u$ to $v$ contains just vertex $u$, which is still white when the value of $u.d$ is set.

If $v$ is a proper descendant of $u$, then by Corollary 22.8, $u.d < v.d$ and so $v$ is white at time $u.d$.

Since $v$ can be any descendant of $u$, all vertices on the unique simple path from u to vin the depth first forest are white at the time u.d.

Assume that there is a path of white vertices from u to v at time u.d, let v be the closest vertex to u along the path that doesn't become a descendant of u.

Let w be the predessor of v in the path, so that w is a descendant of u.

Let w be the predecessor of v in the path, so that w is a descendant of u (w and u may in fact be the same vertex).

By Corollary 22.8, w.f $\leq$ u.f. Since v must be discovered after u is discovered, but before w is finished, we have u.d < v.d < w.f < u.f.

By Theorem 22.7, the interval [v.d, v.f] is contained entirely within the interval [u.d, u.f].

By Corolllary 22.8, v must be after all a descendant of u.

### Four Types of Edges

The depth-first forest $G_{\pi}$ produced by DFS on G is used to define four types of edges.

**Tree edges** are edges in the depth-first forest $G_{\pi}$. Edge (u,v) is a tree edge if v was first discovered when the search reached u.

**Back edges** are edges in the depth-first forest $G_{\pi}$. Edge (u,v) is a back edge if v was discovered before u, but u was not finished before v was discovered.

**Forward edges** are edges in the depth-first forest $G_{\pi}$. Edge (u,v) is a forward edge if u was discovered before v, but v was not finished before u was finished.

**Cross edges** are edges in the depth-first forest $G_{\pi}$. Edge (u,v) is a cross edge if u was discovered before v, and v was finished before u was finished.

### Classification of Edges in DFS

In DFS, when an edge (u,v) is explored, the color of v is helpful in determining the type of this edge.

If the color of v is WHITE, then this edge is a tree edge.

If the color of v is GRAY, then this edge is a back edge.

If the color of v is BLACK and u.d < v.d, then this edge is a forward edge.

If the color of v is BLACK and u.d > v.d, then this edge is a cross edge.

## Theorem 22.10

In a depth-first search of an undirected graph G, every edge is either a tree or a back edge.

### Proof

Consider an arbitrary edge (u,v) in G, and assume that u.d < v.d; if v.f < u.d would consider (v, u).

Then the search must discover and finish v before it finishes u while u is gray, since v is on u's adjacency list.

If it is the first time that the search explores edge (u,v), it is in the direction from u to v, then v is white until that time, for otherwise the search would have explored this edge already in the direction from v to u.

Thus, (u,v) becomes a tree edge.

Then the search explores (u,v) in the direction from v to u, then (u,v) is a back edge, since u is still gray at the time that the edge is explored.

```
DFS(G):
    for each vertex u in G.V:
        u.color = WHITE
        u.pi = NIL
    time = 0
    for each vertex u in G.V:
        if u.color == WHITE:
            DFS-VISIT(G, u)
Iterative-DFS-VISIT(G, u):
    time = time + 1
    u.d = time
    u.color = GRAY
    let uiter be an iterator for list G.Adj[u]
    stack.push(u, uiter)
    while not stack.empty():
        (w, witer) = stack.peek()
        if witer.hasnext()
        if v.color == WHITE
            V.pi = w
            time = time + 1
            v.d = time
            v.color = GRAY
            let viter be an iterator for list G.Adj[v]
            stack.push(v, viter)
        else
            w.color = BLACK
            stack.pop()
            time = time + 1
            w.f = time
```