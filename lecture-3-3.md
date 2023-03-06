# Lecture 19 (3-3)

> !! Understand `MAX-HEAPIFY` well


```
GLOBAL-ALIGNMENT(A, B)
    m = A.length
    n = B.length
    S(m, n) = 0
    for j = n - 1 downto 0
        S(m, j) = S(m, J + 1) - r
    for i = m - 1 downto 0
        S(i, n) = S(i + 1, n) - r
        for j = n - 1 downto 0
            S(i, j) = max(S(i + 1, j + 1) + score(a_{i+1}, b_{j+1}), S(i + 1, j) - r, S(i, j + 1) - r)
```

# Recovering an Optimal Alignment

An optimal alignment is found by a trace back procedure on the table $S$.
An optimal alignment corresponds... TBD...

Initially, the current entry is entry $(0,0)$.

First consider the case where the current entry is entry $(i, j)$.
The recurrences for $S$ are used to determine a new position.

If $i = m$ and $j = n$m then the trace back procedure terminates.

Otherwise, if $(i,j) = S(i+1, j)$, then a new pair for the optimal alignment is a deletion pair $A([i+1],-)$ and the new entry is entry $(i + 1, j)$.

Otherwise, a new pair for the optimal alignment is a subsitution pair $A([i+1], [j+1])$ and the new entry is entry $(i + 1, j + 1)$.

```
TRACEBACK(S):
    let OA be empty
    i = 0, j = 0
    while (i <= m and j <= n)
        if (i == m and j == n)
            break
        if (j == n or i < m and S(i, j) == S(i + 1, j) - r)
            append pair (A[i + 1], -) to OA.
            i++, continue
        if (i == m or S(i, j) == S(i, j + 1) - r)
            append pair (-, B[j + 1]) to OA.
            j++, continue
        append pair (A[i + 1], B[j + 1]) to OA.
        i++, j++
```

## Analyzing the Algorithm

For reference:

```
GLOBAL-ALIGNMENT(A, B)
    m = A.length
    n = B.length
    S(m, n) = 0
    for j = n - 1 downto 0
        S(m, j) = S(m, J + 1) - r
    for i = m - 1 downto 0
        S(i, n) = S(i + 1, n) - r
        for j = n - 1 downto 0
            S(i, j) = max(S(i + 1, j + 1) + score(a_{i+1}, b_{j+1}), S(i + 1, j) - r, S(i, j + 1) - r)
```

Let $d > 0$ be an upper bound on the cost of executing each line once in `GLOBAL-ALIGNMENT`.

The fore loop of lines 4-5 iterates n times.
The running time of lines 1-5 is bounded from above by $3d + 2dn + d$.

One iteration of the for loop on lines 6-9 is bounded from above by $2d + d + 2dn$ and the number of iterations is $m$.

Thus, the running time of `GLOBAL-ALIGNMENT()` is bounded from above by

