# Lecture 15 (2-22)

## Running Time of the algorithm (Maximum Subarray Problem)

Let a constant $d > 0$ be an upper bound on the cost of executing each line once in the algorithm.

Each iteration of lines 6-14 is bounded from above by $9d$.
Thus, the running time of the algorithm is bounded from above by the following expression.

$6d + d + \Sigma_{1 \leq j \leq n} (9d) = 7dn + 9dn + 16dn$ for the constant $c = 16d > 0$ and each $n \geq n_0 = 1$.
Thus, the running time of the algorithm is $O(n)$.

## Overlapping Subproblems

Two subproblems are overlapping if they are the same subproblem that occurs as a subproblem of different problems.

The total number of distinct subproblems is usually a polynomial in the input size.

Dynamic-programming algorithms handle overlapping subproblems by solving each subproblem once and then storing the solution in a table so that it can be accessed in a constant time in solving larger subproblems.

If an algorithm solves the same subproblem repeatedly, then its running time might be exponential in the input size or worse.

```
// An inefficient recursive algorithm for computing
// the maxiumum value of all subarrays of array A.
// max(a, b, c): the maximum of a, b, and c.
RECURSIVE-MAX-SUBARRAY(A, p, r)
    if p == r
        return A[p]
    result = negative infinity
    sum = 0.0
    for k = p to r - 1
        L = RECURSIVE-MAX-SUBARRAY(A, p, k)
        R = RECURSIVE-MAX-SUBARRAY(A, k + 1, r)
        result = max(result, L, R)
        sum = sum + A[k]
    sum = sum + A[r]
    return max(sum, result)
```

> !! We do big-$\Omega$ when we want to prove the algorithm is bad.

Let $d$ be the minimum time of running any line once in the algorithm.

Let $T(n)$ be the worst-case running time of the algorithm on arrays of length $n$.

We obtain the recurrence for $T(n)$ based on the structure of the algorithm:
$\\T(1) \geq d, \\ T(n) \geq d + \Sigma_{k=1}^{n-1} (T(k) + T(n-k))$ for all $n \geq 1$.

It can be shown by induction that $T(n) \geq d * 2^{n-1}$ for all $n \geq 1$.

The running time of an algorithm is at least exponential in the input size.
The reason for the inefficiency is that many subproblems are solved repeatedly.
