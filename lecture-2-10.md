# Lecture 10 (2-10)

## Heaps

Heaps are used in a sorting alogirthm and a priority queue data structure.

A heap is a complete binary tree stored in an array `A[1...A.heap-size]`, where $0 \leq A.leap-size \leq A.length$.

1. In a max heap, for every node $i$ other than root, `A[PARENT(i)] >= A[i]`.

...TBD...

## Height of a Node and Height of a Heap

The height of a node is a heap is the number of edges on the longest simple downward parth from the node to a leaf.

The height of the heap is the height of the root.

## Height of a Heap of size $n$

We show that an $n$-element heap has height $\lfloor \lg n \rfloor$.

The maximum number of nodes in a heap of height $h$ is $2^h - 1$.

The minimum number of nodes in a heap of height $h$ is $2^h - 1 + 1$.

For an $n$-element heap of height $h$, we have $2^h \leq n < 2^{h+1}$.\\
$h \leq \lg n < h + 1$.

Note that $h$ is an integer.
So $h = \lfloor \lg n \rfloor$.

## The numver of leaves in a Heap of size N

The number of non-leaf nodes in an n-element heap is $\lfloor n/2 \rfloor$, and the number of leaf nodes is $\lceil n/2 \rceil$.

Conisder the index of the first leaf node, i.e., $\lfloor n/2 \rfloor + 1$ the index of the node with the smallest index that is a leaf.

...TBD...

## Maintaining the Heap Property

We call `MAX-HEAPIFY` on an array $A$ and an index $i$ when the binary trees roted at `LEFT(i)` and `RIGHT(i)` are max-heaps, but `A[i]` may be samller than its children.

```
MAX-HEAPIFY(A, i)
  lt = LEFT(i)
  rt = RIGHT(i)
  if lt <= A.heap-size and A[lt] > A[i]
    largest = lt
  else
    largest = i
  if rt <= A.heap-size and A[rt] > A[largest]
    largest = rt
  if largest != i
    exchange A[i] with A[largest]
    MAX-HEAPIFY(A, largest)
```

The running time of `MAX-HEAPIFY` on a node of height $h$ is $O(h)$.

## Building a Heap

Previously, we showed that the elements in the subarray $A[(\lfloor n/2 \rfloor + 1)...n]$ are all leaves of the heap, so each of these nodes is a 1-element heap.

The procedure `BUILD-MAX-HEAP` goes through the array and runs `MAX-HEAPIFY` on each node.

```
BUILD-MAX-HEAP(A):
    A.heap-size = A.length
    for i = floor(A.length/2) downto 1
        MAX-HEAPIFY(A, i)
```

### Proving the correctness of `BUILD-MAX-HEAP`

We show that `BUILD-MAX-HEAP` is correct by using the following loop invariant.

At the start of each iteration of the for loop of lines 2-3, each of nodes $i + 1, i + 2, ... n$ is the root of a max-heap.

**Initialization**: Before the first iteration of the loop, $i = \lfloor n/2 \rfloor$ each of the nodes...TBD...

**Maintenance**: Assume that at the start of iteration $i \leq \lfloor n/2 \rfloor$, each of nodes $i + 1, i + 2, ... n$ is the root of a max-heap.

We want to show that the end of iteration, each of node $i$, $i+1, i+2, ... n$ is the root of a max-heap. Decrease $i$ by i in the for loop counter update makes the loop invarianvt hold...

Before the start of each iteration of the loop, the subarray $A[(\lfloor n/2 \rfloor + 1)...n]$ is a max-heap.

**Termination**: After the last iteration of the loop, $i = 0$. By the loop invariant, each of nodes $1, 2, ... n$ is athe root of a max-heap. So is node 1.

## Number of nodes of any Height h

The time taken on a node by `BUILD-MAX-HEAP` is proportional to the height of the node.

We show that the hieghts of most nodes are small.

The height of a node in a heap is the number of edges on the left-child path from the node to the left most leaf node.

Let $i$ be the index of a node of height $\geq h \geq 0$.

Then the index of the left child of this node is $2i$.

Next the index of the left child of this child $2^2 i$.

In general, the index of the leftmost node reached on the left-child path of $h$ edges is $2^hi$.

Thus a node in an n-element heap is of height $\leq h \geq o$ if and only if its index i satisfies $2^h \leq n \lor i \leq n/2^h$. 

Note that the index is an integer, we have $i \leq \lfloor n/2^h \rfloor$.

The number the number of nodes of height $h \geq 0$ is the number of nodes of height $0$ in the resulting heap with $\lfloor n/2^h \rfloor$ nodes, after each node of height less than $h$ is removed.

Using the formula for the number of nodes of height $0$ in a heap with $\lfloor n/2^h \rfloor$ nodes, we conclude that the number of nodes of height $h \geq 0$ is $\lceil \lfloor n/2^h \rfloor \ 2 \rceil \leq \lceil \lceil n / 2^h \rceil / 2 \rceil$.

Thus, the number of nodes of height $\geq h \geq 0$ is $\lfloor n/2^h \rfloor$.

The number of nodes of height $h \geq 0$ is the number of nodes of height $0$ in the resulting heap with $\lfloor n/2^h \rfloor$ nodes, after each node of height less than $h$ is removed.

Using the formula for the number of nodes of height $0$ in a heap with $\lfloor n/2^h \rfloor$ nodes, we conclude that the number of nodes of height $h \ geq 0$ is $\lceil \lfloor n/2^h \rfloor / 2 \rceil \leq \lceil \lceil n / 2^h \rceil / 2 \rceil = \lceil n / 2^{h + 1 } \rceil$.