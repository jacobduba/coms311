# Lecture 7 (2-1)

## Analysis of `MERGE-SORT`

We can show that the algorithm is correct by formulating and proving loop invariants.
The proof is omitted.

Let the running time of `MERGE-SORT` on a sequence of $n$ elements be bounded above by $T(n)$.

Based on the above analysis, we obtain the following recurrence for $T(n)$ for some constnat $d > 0$.

$T(1) = d$

$T(n) = T(\lceil \frac{n}{2} \rceil) + T(\lfloor \frac{n}{2} \rfloor) + dn$ if $n > 1$.

$T(2) = T(\lceil \frac{2}{2} \rceil) + T(\lfloor \frac{2}{2} \rfloor) + 2d = 2T(1) + 2d = 2d + 2d = 4d$

$T(3) = T(\lceil \frac{3}{2} \rceil) + T(\lfloor \frac{3}{2} \rfloor) + 3d = T(2) + T(1) + 3d = 4d + d + 3d = 8d$

Assume that $n$ is a perfect power of 2, i.e., $n = 2^k$ for some $k \geq 0$.

Then the recurrence for $T(n)$ becomes $T(n) = 2T(n/2) + dn$ if $n > 1$.
It also holds by replacing $n$ by $\frac{n}{2}$ and by $\frac{n}{2^2}$.

$T(\frac{n}{2}) = 2T(\frac{n}{2^2}) + d(\frac{n}{2})$ if $\frac{n}{2} > 1$.

$T(\frac{n}{2^2}) = 2T(\frac{n}{2^3}) + d(\frac{n}{2^2})$ if $\frac{n}{2^2} > 1$.

Repeatedly replace the left side by the right side, we obtain $T(n) = 2T(\frac{n}{2^2}) + dn = 2[2T(\frac{n}{2^2}) + d(\frac{n}{2})]+ dn$

$ = 2^2 T(\frac{n}{2^2}) + 2dn$

$= 2^h T(\frac{n}{2^h}) + hdn$ where $1 \leq h \leq k$.

$= 2^kT(\frac{n}{2^k}) = 2^kT(1) + kdn =$ **TBD**

Another way to understand $T(n)$:

$T(n) = 2T(n/2) + dn$ if $n > 1$.

$T(2) = 2T(2/2) + d * 2 = 2T(1) + 2d$

$T(2^2) = 2T(2^2/2) + d * 2^2 = 2^2T(2) + 2^2d$

$T(2^3) = 2T(2^3/2) + d * 2^3 = 2^3T(2^2) + 2^3d$
= 4d
$T(2^k) = 2T(2^k/2) + d * 2^k = 2^kT(2^{k-1}) + 2^kd$


If $n$ is not a perfect power of 2, then we have $2^k < n < 2^{k+1}$ for some k. 

It can be shown by mathematical induction that $T(n)$ is monotonically increasing:

If $m \leq n$, then $T(m) \leq T(n)$.

Then we have:

$T(n) \leq T(2^{k+1}) \leq 2d2^{k+1}(k+1) = 4d2^k(1+k)$

$\leq 4dn(1+\log n) \leq 4dn(\log n + \log n) = 8dn \log n$, if $n > 2$ with $c = 8d$

Thus, $T(n)$ is in $O(n \log n)$.

## Understanding Recurrences

The recurrence is used to obtain an upper bound $T(n)$ on the running time of a recursive algorithm for any input size $n$ as follows.

$T(1) = d = 2d * 1 - d$

$T(2) = T(1) +T(1) + d = d + d + d = 3d = 2d * 2 - d$

$T(3) = T(2) + T(1) = ...$

And so on...