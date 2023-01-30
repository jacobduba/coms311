# Lecture 6 (1-30)

## Growth of Functions

Big-O functions in ascending order of growth rates

$O(1), O(log_2n), O(n), O(nlog_2n), O(n^2), O(n^3), O(2^n)$

Algoirthms with $O(nlog_2n)$ are acceptable for large n.

Algorithsms with $O(n^2)$ are slow for large n.

### Example !!!

Show that $nlog_2n$ is not in $O(n)$.

We use proof by contradiction.
We assume that $nlog_2n$ is in $O(n)$.

By definition, there exist positive constants $c$ and $n_0$ such that:
$nlog_2n \leq cn$ for all $n \geq n_0$.

Dividing each side by n, we have
$log_2n \leq c$ for alll $n \geq n_0$.

Using the above, we obtain
$n = 2^{log_2n} \leq 2^c$ for all $n \geq n_0$.

This is false for any $n \geq max(n_0, 1 + \lceil 2^x \rceil) > 2^n$

This contradiction results from the wrong assumption.

## Algorithm Design Technique: Divide and Conquer

In a recursive algorithm, we first check if an instance if small enough.
If so, we obtian the solution in a straightfoward manner.
Otherwise, we solve it by following a divide-and-conquer strategy., which consists of three steps.

**Divide**: And isntance of the problem is divided into a number of smaller isntances of the same name. 

**Conquer**: The smaller instances are solved recursively.

**Combine**: The solutions to the smaller instances are conbined into the solution for the original instance.

## Merge Sort

We use the divide and conquer technique to design an algorithm (called Merge Sort) for sorting a sequence of n items.

**Divide**: A sequence of n items is divided into two subsequences of $\lceil \frac{n}{2} \rceil$ and $\lfloor \frac{n}{2} \rfloor$ items, respectively.

**Conquer**: The two subsequences are sorted recursively using merge sort.

**Combine**: The two sorted subsequences are combined to form the sorted sequence.

Note that $n = \lceil \frac{n}{2} \rceil + \lfloor \frac{n}{2} \rfloor$.

## Merge-sort

Let $A[1..n]$ be an array of $n$ elements.

The array is sorted by calling `MERGE-SORT(A, 1, n)`

`MERGE-SORT(A, p, r)` sorts the elements in the subarray `A[p..r]` by dividing `A[p..r]` into `A[p..q]` and `A[q+1..r]`, sorting each subarray recursively and then merging the sorted sub arrays into one sorted subarray where $q = \lfloor \frac{p + r}{2} \rfloor$.

Let $m = r - p + 1$ ne te size of `A[p..r]`.

It can be shown that the size of `A[p..q]` and `A[q+1..r]` are $\lceil m/2 \rceil$ and $\lfloor m/2 \rfloor$ respectively.

For example, if $p = 2s$ and $r = 2t$, then $q = \lfloor \frac{(2t + 2s)}{2} \rfloor = s + t$.

$q-p+1 = (s+t) - 2s + 1 = t - s + 1 = \lceil \frac{2t-2s+1}{2} \rceil = \lceil \frac{m}{2} \rceil$

$r - (q + 1) + 1 = 2t - (s + t + 1) + 1 = t - s = \lfloor \frac{(2t-2s+1)}{2} \rfloor = \lfloor \frac{m}{2} \rfloor$

Proofs for other cases omitted: one of $p$ and $r$ is even and the other is odd, or both are odd.

```
// Sorts the elemetns in the subarray A[p..r]
MERGE-SORT(A, p, r)
  if p < r
    q = floor( (p + r) /2 )
    MERGE-SORT(A, p, q)
    MERGE-SORT(A, q+1, r)
    MERGE(A, p, q, r)

// Takes the two sorted subarrays A[p..q] and A[q+1..r] 
// and merges them into a single sorted subarray A[p..r]
// and saves it in the subarray A[p..r]
MERGE(A, p, q, r)
    n1 = q - p + 1 // the size of A[p..q]
    n2 = r - q // The size of A[q+1..r]
    let L[1..n1+1] and R[1..n2+1] be new arrays
    for i = 1 to n1
        L[i] = A[p+i-1]
    for j = 1 to n2
        R[j] = A[q+j]
```