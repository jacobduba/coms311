# Lecture 2 (1-20)

## How to Develop Algoruthm Design Skils

- Know pseudocode notations and conventions.
- Trace the execution of an algorithm on an instance to determin if it is correct on the instance.
- If it is incorrect, fix the algorithm and repeat it on another instance.
- Master correctness proof techniques.
- Know how to determine the running time of an algorithm.
- Understand common algorithm design techniques.

## Iterative Algorithms

- INSERTION-SORT is an iterative algorithm composed of loops.
- Quick Sort and Merge Sort are often presented using recursive procedures, which call themselves on smaller instances.
- Unlike resursive algorithms, iterative algorithms do not suffer from a memory problem called runtime stack overflow.
- INSERTION-SORT is slow, but does not run out of memory on large instances.

## Loop Invairants

- Loop invariants are used to show that algorithms are correct.
- A loop invariant for Insertion Sort:
    - At the start of each iteration of the outer loop, the subarray A[1] through A[j-1] consists of the elements originally in the subarray, but in sorted order.

## Justification

- **Initialization**: It is true when j = 2, since the subarray A[1..j-1] consists of just the element A[1], which is by definition sorted.
  - It is true before the first iteration of the loop.
- **Maintenance**: By the assumption, A[1..j-1] is sorted. Lines 4-8 (of the insertion sort from [[1-18]]) inserts A[j] into the sorted sequence A[1..j-1].
  - If it is true before an iteration of the loop, it remains true before the next iteration.

## Justification

### Case 1

If $A[j] \geq A[j-1]$, then by the assumption that $A[1..j-1]$ is sorted, we conclude that $A[j]$ is equal to or larger than every element in $A[1..j-1]$.
So line 5 is false with $i = j - 1$, and A[j] is placed at position $i + 1 = j - 1 + 1 = j$;

### Case 2

If $A[j] < A[1]$, then by the assumption that $A[1..j-1]$ is sorted, we conclude that $A[j]$ is smaller than every element in $A[1..j-1]$.
So line 5 is true for each $i > 0$, and $A[j]$ is placed at position $i + 1 = 0 + 1 = 1$, with the previous $A[1..j-1]$ moved to $A[2..j]$.

### Case 3

Otherwise, we conclude that $A[1] \leq A[j] < A[j-1]$.
Note that $A[1] \leq A[j]$ is the negation of $A[j] < A[1]$ and that $A[j] < A[j-1]$ is the negation of $A[j] \geq A[j-1]$.
Since $A[1..j-1]$ is sorted, there exists an index $k$, $1 \leq k \leq j-2$, such that $A[1] \leq A[2] \leq ... \leq A[k] \leq A[j] < A[k+1] \leq ... \leq A[j-1]$.
So A[j] is placed at position $i+1=k+1$, with previous $A[k+1..j-1]$ moved to $A[k+2..j]$.
Thus, at the end of the current iteration, $A[1..j]$ is sorted.

## Termination

At the end of the last iteration with j = n, $A[1..n]$ consists of th elements in the array, but in sorted order.