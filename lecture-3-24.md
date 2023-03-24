# Lecture 3-24

## More on the proof

Thus, we conclude that $v.d = \delta(s,v)$ for all $v \in V$.

All vertices reachable from s must be discovered, for otherwise they would have $\infty = v.d \leq \delta(s,v)$, leading to a contradiction.

Finally, note that if $v.\pi = u$, then $v.d = u.d + 1$.

Thus, we can obtain the shortest path from $s$ to $v$ by taking the shortest path from $s$ to $v.\pi$ and then traversing the edge ($v.\pi, v$).

## Running Time of BFS

We analyze the running time...

... Because the adjacency list of each vertex is scanned when the vertex is dequeued, each adjacency list is scanned when the vertex is dequeued, eac

## Breadth-First Tree

BFS builds a breadth-first tree by using the $\pi$ attributes.

For a graph $G = (V,E)$ with source $s$, the **predecessor subgraph**

## Depth-First Search

**Depth-first search** (DFS) is another simple search algorithm for answering basic questions about a graph.
Below are two applications of this algorithm.

We can use BFS to perform a topological sort of a directed acyclic graph (DAG).
A *topological sort* of a DAG $G = (V,E)$ is a linear ordering of all its vertices such that if $G$ contains an edge $(u,v)$, then $u$ appears before $v$ in the ordering.

We can use DFS to decompose a directed graph into strongly connected components.
A strongly connected component of a directed graph $G = (V,E)$ is a maximal set of vertices $C \subseteq V$ such that for every pair of vertices $u$ and $v$ in $C$, vertices $u$ and $v$ are reachable from each other.

## DFS

In dept-first search (DFS), we start a new search at a discovered vertex immediately after the vertex is reached.

The search explores edges out of the most recently reached vertex $v$ that still has unexplored edges leaving it.

Once all of v's edges have been explored, the search returns to explore edges leaving the vertex from which $v$ is reached.

This process continues until we have discovered all the vertices reachable from the first source vertex.