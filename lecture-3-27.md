# Lecture 3-27

Like BFS, whenever FBS discovered a vertex $v$ from scanning the adjacent list of an already discovered vertex $u$.

...

BFS colors vertices like BFS, guaranteeing that each vertex ends up in exactly on dept-first tree so that these trees are disjoint.

In addition, DFS timestamps each vertex $u$ twice: the first timestamp $u.d$ records when $u$ is first discovered and colored gray, and the second timestamp.

Recursive DFS

```
DFS(G):
for each vertex u in G.V:
    u.color = WHITE
    u.pi = NIL
time = 0
for each vertex u in G.V:
    if u.color == WHITE:
        DFS-VISIT(G, u)
    
DFS-VISIT(G, u)
    time = time + 1
    u.d = time
    u.color = GRAY
    for each v in G.Adj[u]:
        if v.color == WHITE:
            v.pi = u
            DFS-VISIT(G, v)
    u.color = BLACK
    time = time + 1
    u.f = time
```

Consider intervals [u.d, u.f] for the discovery time u.d and finish time u for each vertex u.

If two intervals overlap, then one is nested within the other...

### Theorem 22.7 (Parenthesis Theorem)

If any depth-first search of a (directed or undirected) graph G = (V, E) for any two vertices u and v, exactly one of the following three conditions hold:

1. The intervals [u.d, u.f] and [v.d, v.f] are disjoint. Neither u nor b is a descendant of the other in the dept-first forest.

2. The interval [u.d, u.f] is contained entirely within the interval [v.d, v.f] and u is a descendant of v in a depth-first state.

3. The interval [v.d, v.f] is contained entirely within the interval [u.d, u.f] and v is a descendant of u in a depth-first state.

## Running Time of DFS

We determine the running time of DFS by using aggregate analysis, in which the total running time for a sequence of operations is analyzed.

The loops on lines 1-3 and lines 5-7 of DFS take O(V) time, exclusive of the time to execture calls to DFS-VISIT.

DFS-VISIT is called exactly once of each vertex u, because any vertex on which DFS-VIRIST is invoked must be white and is colored gray at the beginning of the call.