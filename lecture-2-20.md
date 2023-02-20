# Lecture 14 (2-20)

## Hash functions 

> !! HW 2, Q3 !!

We study the division method for creating hash functions.

In the division method, a key k is mapped to one of m slots but using the remainder of k divided by m:

$h(k) = k \mod m$

For example, $h(40) = 40 \mod 31 = 9$ since $40 = 1 * 31 + 9$

Certain values of m are avoided.

For example, a power of 2 is not a good choice for $m$.
If $m = 2^p$, then $h(k)$ is simply the $p$ lowest-order bits of $k$, so the other bits of the key are not used in computing $h(k)$.

## Dynamic Programming

Dynamic programming, like divide-and-conquer, solves problems by combining the solutions to subproblems.

In divide-and-conquer, the problem is partitioned into disjoint problems in a top-down fashion.

In dynamic programming, however, subproblems of increasing sizes are considered in a bottom-up fashion by solving each subproblem once and saving its solution in a table, where the solution to a large subproblem is obtained by combining the solutions to smaller subproblems.

Dynamic programming is often applied to optimization problems, which can have many possible solutions, each associated witha a value.
The goal is to find a solution with the optimal (minimum or maximum) value, an optional solution to the problem.

## Main Steps of Dynamic Programming

1. Express a larger optimal solution using smaller ones.
2. Develop a recurrence for the value of an optimal solution.
3. Compute and save the values of optimal solutions to subproblem of increasing size in a bottom up fashion.
4. Construct an optimal solution from the saved values.

## The Maximum-Subarray Problem

For an array `A[1..n]` of positive and negative values, the score `S(i,j)` of a subarray `A[i..j]` with $i \leq j$ is the sum of all values in the subarray:
$S(i,j)=\sum_{k=i}^j A[k]$ for $i \leq j$.

The maximum-subarray problem is to find a subarray `A[i..j]` with $i \leq j$ such that its score is the maximum over all subarrays.
This subarray is called an optimal subarray.

We apply dynamic programming to this problem to develop a linear time algorithm.

## Structure of an Optimal Subarray

An optimal subarray can end at any of the $n$ positions in the array $A$.

For each $j$, $1 \leq j \leq n$, define `v[j]` to be the maximum score of all subarrays ending at index $j$ of $A$:

$v[j] = \max_{i \leq i \leq j} S(i,j)$.

Then the value of an optimal subarray is $\text{maxv} = \text{max}_{1 \leq j \leq n} v[j]$.

## Structure of an Optimal Solution

Calculate the scores of all subarrays ending at index 4 in the example array..

$S(1,5) = (-15) + 20 + 35 + (-5) + 25 = 60\\
S(2,5) = 20 + 35 + (-5) + 25 = 75\\
S(3,5) = 35 + (-5) + 25 = 55\\
S(4,5) = (-5) + 25 = 20\\
S(5,5) = 25$

So the subarray `A[2..5]` is one with the maximum score ending at index 5.
This subarray consists of the subarray `A[2..4]` and the value `A[5]`.
We can confirm that the subarray `A[2..5]` is a subarray ending at index $4$ withthe maximum score `v[4] = 50`. :w

In contrast, the subarray `A[1..4]` ends at index 4 with a score of 35, which is less than the maximum score `v[4] = 50`.
So the subarray `A[1..4]` is not optimal for index 4.

Appending `A[5]` to `A[1..4]` on the right side results in a subarray `A[1..5]` ...TBD...

Consider a subarray `A[h..j]` with the value `v[j]`, which is a subarray ending at index $j$ with the maximum score.

If $h = j$, then we have `v[j] = A[j]`.
Otherwise, $h < j$, we conclude that `A[1..j-1]` is a subarray ending at index $j-1$ with the maxiumum score `v[j-1]`, and we have `v[j] = v[j-1] + A[j]`.

This is because `A[h..j]` is optimal for index $j$ with the maximum score `v[j]`.

Since both `A[j]` and `v[j-1] + A[j]` are the scores of subarray ending at index $j$, and since `v[j]` is the maximum score of all subarrays ending at index $j$, we have
$v[j] \geq A[j]$ and $v[j] \geq v[j-1] + A[j]$.

Combining these observations together, we have $v[j] = \text{max} \{A[j], v[j-1] + A[j]\}$.

```
FIND-MAXIMUM-SUBARRAY-IN-LINEAR-TIME(A)
    n = A.length
    v = 0 // No need to use the array v[1..n]
    vstart = 1
    maxv = negative infinity // global maxiumum
    max-start = max-end = 0 // its start and  
    for j = 1 to n
        v = v + A[j] // v[j-1] + A[j]
        if v < A[j]
            v = A[j]
            vstart = j
        if v > maxv
            maxv = v
            max-start = vstart
            max-end = j
    return (max-start, max-end, maxv)