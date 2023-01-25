# Lecture 1 (1-18)

## How to succeed in this course

- Do the reading tasks given on Canvas for each week.
- Attend lecture
- Start early on each assignment
- Seek help if you cannot make progress after repeated attempts
- Produce correct solution on your own to show you understand the material

## Insertion Sort

Input: An array of n items that can be compared

Output: An Array A of items in ascending order

```
A[1] <= A[2] <= A[3] <= ... <= A[n]
```

Idea: For each j from 2 to n, place A[j] at a proper plae in A[1] through A[j].

```
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

```
    A: 8 | 5   1   3   6
index: 1   2   3   4   5
    j:     2

    A: 5   8 | 1   3   6
index: 1   2   3   4   5
    j:         3

    A: 1   5   8 | 3   6
index: 1   2   3   4   5
    j:             4

    A: 1   3   5   8 | 6
index: 1   2   3   4   5
    j:                 5

    A: 1   3   5   6   8 |
index: 1   2   3   4   5
    j:                     6
```