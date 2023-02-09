# Lecture 8 (2-6)

## Changing variables

Consider $T(n)$ defined by the recurrence
$T(n) = 2T(2^{\lfloor(\log n)/2\rfloor}) + \log n$.

We simplify the recurrence by changing the varaible $n = 2^m$.
$T(2^m) = 2T(2^{\lfloor m/2\rfloor}) + m$.

By defining $S(m) = T(2^m)$, we have obtained the new recurrence
$S(m) = 2S(\lfloor m/2 \rfloor) + m$.

It can be shown by mathematical induction that $S(m) \in O(m \log n)$.

Changing back from S(m) to T(n), we obtai,
$T(n) = T(2^m) = S(m) = O(m \log n) = O(\log n \log \log n)$.

## The master method for solving recurrences

The master method is used to determine the running time $T(n)$ of an algorithm that divides a problem of size n into a sublproblems, 
each of size $\lceil n/b \rceil$ for some constant $a \geq 1$ and $b > 1$.

The a subproblems are solved recursively, each in $T(\lceil n/b \rceil)$ time.
Let asymptotically positive function $f(n)$ denote the cost of dividing the problem of contianing the results of subproblems.

Then $T(n)$ is defined by the following recurrence.
$T(n) = aT(\lceil n/b \rceil) + f(n)$, or $T(n) = aT(\lfloor n/b \rfloor) + f(n)$.

> We use floors in the textbook, but ceils can be handled by the master therom.

Let $f(n)$ and $T(n)$ with positive contants $a$ and $b$ be defined in the above recurrence.

1. If $f(n) = O(n^{\log _b a - \epsilon})$ for some constant $\epsilon > 0$, then the running time of the algorithm is $T(n) = \Theta(n^{log _b a})$.
2. If $f(n) = \Theta(n^{\log _b a} \log ^k n)$ for some constant $k \geq 0$, then
$T(n) = \Theta(n^{\log _b a} \log ^{k+1} n)$.
3. If $f(n) = \Omega(n^{\log _b a + \epsilon})$ for some constant $\epsilon > 0$, and if
$af(\lceil n/b \rceil) \leq cf(n)$ for some constant $c > 0$, then all sufficiently large $n$, then $T(n) = \Theta(f(n))$.
