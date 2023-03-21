# Lecture 11 (2-13)

The running time of `MAX-HEAPIFY` on a node of height $h$ is bounded by $dh$ for a constant $d > 0$.

Thus the running time of `BUILD-MAX-HEAP` is bounded from above by 

$= \Sigma^n_{i=1} (d * \text{height}(i))\\
= \Sigma^{\lg n}_{h=0} (\text{number-of-nodes}(i) * dh)\\
\leq \Sigma^{\lg n}_{h = 0} (\lceil \frac{n}{2^{h+1}} \rceil * dh) \leq \Sigma^{\lg n}_{h = 0} (\frac{n}{2^{h+1}} + 1) * dh\\
\leq (dn/2)(\Sigma^{\lg n}_{h = 0}\frac{2}{2^h}) + \Sigma^{\lg n}_{h=0}dh\\
\leq (dn/2)(\Sigma^{\infty}_{h=0} \frac{h}{2^h}) + \Sigma^{\lg n}_{h=0}dh\\
\leq (dn/2)(\frac{1/2}{(1-1/2)^2}) + d(\lg n)^2 \leq (dn/2)2 + dn = 2dn$

Thus, we can build a heap from an array in linear time.

> In this proof, we used the forumla (A-8) in the textbook: $\Sigma^{\infty}_{k=0} = \frac{x}{1-x}^2$ for $|x| < 1$.

> **!!!** ON THE EXAM, you may need to remember $1 + 2 + 3 + ... + n = \frac{n(n+1)}{2}$.

## Heapsort

We designed an algo called Heapsort using `BUILD-MAX-HEAP` to build a max-heap on the array `A[1...n]` with `n = A.length`.

Then we exchange `A[1]` with `A[n]`, decrease `A.heap-size` by 1, call `MAX-HEAPIFY(A,1)` to restore the max-heap property, and repeat the process until `A.heap-size = 1`.

```
HEAPSORT(A):
    BUILD-MAX-HEAP(A)
    for i = A.length downto 2
        exchange A[1] with A[i]
        A.heap-size = A.heap-size - 1
        MAX-HEAPIFY(A, 1)
```

## Analyzing `HEAPSORT`

`BUILD-MAX-HEAP` takes $O(n)$ time. The loop on lines 2-4 takes $n-1$ iterations, each of which takes time in $O(\lg n)$ The loop on lines 2-4 takes $n-1$ iterations, each of which takes time in $O(\lg n)$.

Thus, `HEAPSORT` takes time in $O(n \lg n)$.

## Lower Bound for Sorting

We show a lower bound for sorting on a model of computation that allows only comparisons between elements.

Let $\langle a_1, a_2, ..., a_n \rangle$ be an array of $n$ distinct elements. 
The model only allows the following comparisons between two elements $a_i$ and $a_j$ to determine their relative order: $a_1 < a_j, a_i \leq a_j, a_i = a_j$, or $a_i > a_j$.

This model deos not alow other operations (such as inspecting the values of the elements) to gain their order information.

We prove a lower bound for a restricted version of sorting where all the input elements are distinct.

Under this resistration, comparisons of th eform $a_i = a_j$ are useless, sot hey are not allowed.
Thus, we assume that all comparisions of the form $a_i \leq a_j$ becasue the comparisons $a_i \leq a_j, a_i \geq a_j, a_i > a_j,$ and $a_i < a_j$ give the same order information about $a_i$ and $a_j$.

## Decision Trees

Any sorting algorithm take thats an input sequence $\land a_1, a_2, ..., a_n \rang$ on the comparison model of computation can be represented by a decision tree.

Each internal node in the decision tree is of the form $i : j$ for some $i$ and $j$ in the range $i \leq i$ in the range $1 \leq i, j \leq n$.
The left subtree of the node performs subsequent comparisons whe $a_i \leq a_j$ and the right subtree of the node performs subsequent comparisons when $a_i > a_j$. 

Each leaf node in teh decision tree is associated with a permutation $\lang \pi(1), \pi(2), ... \pi(n) \rang$, where arriving in the node means that the ordering $\lang a_{\pi}(1), a_{\pi}(2), ... a_{\pi}(n) \rang$ is reported by the sorting algorithm

If the sorting algorithm is correct, then the decision tree has to have at least $n!$ reachable leaf nodes, each corresponding to one of the $n!$ permutations.