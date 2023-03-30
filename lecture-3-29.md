# Lecture 3-29

## Discovery and Finishing Times Have Parenthesis Structures

Consider intervals [u.d, u.f] for the discovery time u.d and finishing time u.f of each vertex u.

If two intervals overlap...

## Theorem 22.7 (Parenthesis Theorem)

In any depth-first search of a (directed or undirected) graph G = (V,E) for any two vertices u and, exactly one of the following three conditions holds.

The intervals [u.d, u.f] and [v.d, v.f] are entirely disjoint, and neither u nor v is a descendant of the other in the dept-first forest.

The interval [u.d, u.f] is contained entirely within the interval [v.d, v.f] and u is a descendant of v in a dept-first tree.

The interval [v.d, v.f] is contained entirely within the interval [u.d, u.f] and v is a descendant of u in a depth-frist tree.

### Proof

Consider the case in which u.d < v.d. If v.d < u.f, then v was discovered while u was gray, indicating that is descendant of u.

Moreover, because v was discovered more recently than u, all of its outgoing edges are explored, and the search at v is finished before the search of u.

Thus, the interval [v.d, v.f] is entirely contained within the interval [u.d, u.f].

If u.f < v.d, then u.d < u.f < v.d < v.f so the intervals [u.d, u.f] and [v.d, f.f] are disjoint.

Since the intervals are disjoint, neither vertex was discovered while the other vertex was gray, so neither vertex is a descendant of the other.

The case where v,d < u.d can be handled similiarly.
