# Lecture 9 (2-8)

## Using the master therom

### Case d

In case (d), $f(n) = n^2 \log n = \Theta (n ^{\log _b a} \log n)$.
So case 2 applies to the function $f(n)$ with $k=1$. So we have the solution

TBD

### Case e

$f(n) = n^2 / \log n = o(n^2)$.
The $\log n$ is asymptotically less than $n^\epsilon$ for any $\epsilon > 0$.
That is, $\log n = o(n^\epsilon)$  for any positive constant $\epsilon$.
It follows that $1 / \log n = \omega(1 / n^\epsilon)$ and that $n^2 / \log n = \omega(n^2 / n^\epsilon)$.
Thus there exists no constant $\epsilon > 0$ such that $n^2 / \log n$ is in $O(n ^{log _b {a - \epsilon}}) = O(n^{2 - \epsilon})$. 
So case 1 does not apply to the function $f(n)$.
Note that case 2 does not apply either, because $n^2 / \log n = \Theta(n^{\log _b a \log ^k})$ with $k = -1$.
$k$ has to be nonnegative for case 2 to apply.

## Full Binary Tree

The dept of a node, also referred to as the level of a node, is the lenght of the path from the root to the node.

A full binary tree is a binary tree in which every lead has the same depth and every non-lead node (interal node) has exactly two children.

A full binary tree of depth d has a total of $2^{d+1} - 1$ nodes.

> The depth of a binary tree is the amount of nodes between the top and the leaf.

## Inductive proof

* In a tree of depth 0, the number of nodes is $2^{0+1} - 1 = 1$.
* In a tree of depth 1, the number of nodes is $2^{1+1} - 1 = 3$.
* In a tree of depth 2, the number of nodes is $2^{2+1} - 1 = 7$.

Assume that a full binary tree of depth d has $2^{d+1} - 1$ nodes.

A full binary tree of depth $d$ consists of a root node, a left full binary tree of depth $d-1$, a right full binary tree of depth $d-1$.

Then the total number of nodes in the full binary tree of depth $d$ is $2^{d+1} - 1 = 2^{d+1} - 1 + 2^{d} + 2^{d} = 2^{d+1} + 2^{d} - 1$.

## Complete binary trees

A binary tree is compelte if it is full through the next-to-lowest level and all of the leaves at the lowest level are as far to the left as possible.

It is possible to store a complete binary tree in an array.

A complete binary tree is stored in an array `A[1...A.length]` such that array indexes are used to find the children of the node.

The root of the tree is at index $1$.
For a node at index $i$, we can easily obtain the indices of its parent, left child, and right child.

* **PARENT**: return $\lfloor i/2 \rfloor$
* **LEFT**: return $2 * i$
* **RIGHT**: return $2 * i + 1$