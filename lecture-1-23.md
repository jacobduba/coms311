# Lecture 3 (1-23)

## Some measure of the quality of algorithms

- The amount of time taken by algorithm.
- The amount of memory.
- The amount of network bandwidth.
- The amount of effort to code an algorithm.

Under each measure, a better algorithm takes a smaller amount of resource or effort.

We will focus on techniques for estimating the running time of an algorithm into a program.
However, the techniques can be applied to other measures.

## Concepts of Algorithms

- A problem consists of a large number of instances.
- An instance of the sorting problem is a sequence of numbers: 5, 57, 23, 49, 34.
- The size of an input is the *input size*, defined as the amount of memory needed to store the instance.
- An input instance consists of n numbers with each number taking 64 bytes. The input size is $64 * n$.
- We only need to compute the input size within a constant factor.

## Running Time of an Algorithm

- The running time of an algorithm on an instance is the number of primitive instructions excecuted.
- An algorithm may take more time on some instances than other instances of the same size.
- The running time of an algorithm may be expressed as the function of the input size obtained by taking the average over all possible instances of the same size.
However, an average case analysis is typically difficult.
- Thus we often focus on finding the worst-case running time of an algorithm, the longest running time on any instance of size *n*, which is expressed as a function (E.g. 20n^2 + 10n + 5) of the input size n.
- Here the function 20n^2 + 10n + 5 is an upper bound on the amount of time taken by the algorithm on any instance of input size n.
- Our mathematical analysis based on RAM model can only determine the running time of an algorithm on a real machine within a constant factor. 
- The exact amount depends on  a particular real machine.
- Thus there is no need to determine the exact amount of time taken by an algorithm on the RAM model.
- Thus we can say that the running time of the algorithm is proportional to $n^2$ instead of $20n^2+10n+5$ as $n^2$ is a simple function of n.

> Let's practice...

```
An algorithm may take more time on some instances than other instances of the same size.
The running time of an algorithm may be expressed as the function of the input size obtained by taking the average over all possible instances of the same size. However, an average
n = A.length
for j = 2 to n // j goes from 2, 3, ..., n
    key = A[j]
    // Insert A[j] into the sorted sequence A[1...j - 1]
    i = j - 1
    while i > 0 and A[i] > key
        A[i + 1] = A[i]
        i = i - 1
    A[i + 1] = key
```

## Analysis of Insertion Sort

- Let a constant d by an upper bound on the time (cost) of any line executed once.
- The outer loop consists of three statements and a while loop with two-statements in its body.
- The while loop iterates at most $j-1$ times, and each iteration of the while loop checks the loop condition once and runs each of the two statements in the loop body once, with the cost of each iteration bound.
- So the cost of the while loop is bounded by 3d x (j - 1) + d where the last term d is an upper bound on the cost of evaluating the while loop plus the upper bound of 4d on the loop condition.
- The worst-case running time T(n) of the algorithm is bounded by the following expression:

$$T(n) \leq d + \sum_{j=2}^{n} (4d + 3d(j-1) + d) + d\\
= 2d + \sum_{j=2}^n(5d)+3d(\sum_{j=2}^n(j-1))\\
= 2d + 5d(n-1) + 3d(1 + 2 + ... + (n - 1))\\
= 2d + 5d(n-1) + 3d(\frac{(n-1)n}{2})$$