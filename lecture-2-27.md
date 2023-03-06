# Lecture 17 (2-27)

What to expect for Exam 1:

* Solving recurrence relation — induction.
* Solving runtime
* Finding relationship between $f(n)$ and $g(n)$.
    * Given an array, know how to build the heap
        * Linear memory time
* Hash function

## A Dynamic Programming Algorithm

Let two sequences of length $m$ and $n$ be stored in two character arrays `A[1..m]` and `B[1..n]`.

Dynamic programming is used to develop an algorithm for computing an optimal global alignment of `A[1..m]` and `B[1..n]`.

## The Structure of an Optimal Alignment

For $0 \leq i \leq m$ and $0 \leq j \leq n$, `A[i+1..m]` is a suffix of `A[1..m]` and `B[j+1..n]` is a suffix of `B[1..n]`.
Assume that `A[i+1..m]` and `B[j+1..n]` denote the empty sequence.

A table $S$ is introduced, $S(i,j)$ is the maximum score of all alignments of `A[i+1,m]` and `B[j+1,n]`.
Thus, $S(0,0)$ is the score of an optimal alignment of `A[1..m]` and `B[a..n]`.

$S(i,j)$ is the score of an optimal alignment of the two suffixes `A[i+1..m]` and `B[j+1..n]`.

This alignment is denoted by `[A[i + 1..m], B[j + 1..n]]`.

The first aligned pair of this optimal alignment has to be one of the following aligned pairs:

* A substitution pair
* A deletion pair
* An insertion pair

