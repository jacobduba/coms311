# Lecture 12 (2-15)

## Some **!! Helpful !!** Log Identities

- $\lg g(n) = \Theta (n \lg n)$
- $n! = \Theta (n^n)$

## Proving fastest sorting is $O(n \lg n)$

Any sorting algorithm on the comparison model of computation requires $\Omega (n \lg n)$ comparisons in the worst case.

**Proof**: Any sorting algorithm on the comparison model of computation is represented by a decision tree in which each of the $n!$ permutations appears as a reachable leaf.

The worst-case number of comparisions performed by the sorted algorithm is the height of its decision tree.

Let the decision tree be of height $h$ with $I$ leaf nodes, where $n! \leq I$.
We can show by induction that a binary tree of height $h$ has no more than $2^h$ nodes.

Thus, we have $n! \leq 2^h$.

By taking logarithms on each side, we obtain
$h \geq \lg n! \geq \lg[1 * 2 * 3 * ... * (\lfloor n/2 \rfloor) * *\lfloor n/2 \rfloor + 1) * ... * (n - 1) *n]$
Replace i by 2 for each i in the range $3 \leq i \leq \lfloor n/2 \rfloor$

$\geq \lg [ (1/2) * 2 * ... * 2 * (\lfloor n/2 \rfloor + 1) * ... * n]$ (No. of 2's is $\lfloor n/2 \rfloor$) 
(No. of 2's is $\lfloor n/2 \rfloor$)  

$\geq \lg [ (1/2) * 2^{n/2} * (\lfloor n/2 \rfloor + 1) * ... * n]$
 (Note $\lfloor n/2 \rfloor + 1 \geq n$) 

$\geq \lg [ (1/2) * 2^{\lfloor n/2 \rfloor} * (\lceil n/2 \rceil)^{\lceil n/2 \rceil}]$
 (No. of $\lceil n/2 \rceil$'s is in $\lceil n/2 \rceil$) 
Replace $i$ by $\lceil n/2 \rceil$ for each $i$ in the range $\lceil n/2 \rceil + 1 \leq i \leq n$

$\geq \lg [ (1/2) * 2^{n/2-1} * (n/2)^{n/2}]$

$\geq \lg [ (1/4) * 2^{n/2} * (n/2)^{n/2}]$

$= \lg [ (1/4) * n^{n/2} ]= \lg (1/4] + \lg(n^{n/2}) = -2 + (n/2)\lg n = (n/4) \lg n - 2 + (n/4) \lg n \geq (1/4) n \lg n$ for all $n \geq 6$

$= (n/4) \lg n - 2 + (n/4) \lg n \geq (1/4) n \lg n$ for all $n \geq 6$

Thus, $h$ is in $\Omega (n \lg n)$.

> Heapsort and merge sort are asymptotically optimal sorting algorithms on the comparison model of compuation.

## Using Limits in Asymptotic Analysis

The formal definition of big $O$ bears a similarity to that of the limit of a sequence in Calculus.

The following rules relate the formal definition of a limit to those of big $O$ and $\Omega$ and big $\Theta$.

Let $f(n)$ and $g(n)$ be asymptotically non-negative functions.

If $\lim_{n \rightarrow \infty} f(n) / g(n) = 0,$ then $f(n)$ is in $O(g(n))$.

If $\lim_{n \rightarrow \infty} f(n) / g(n) = \infty,$ then $f(n)$ is in $\Omega(g(n))$.

If $\lim$ ... TBD ...

## Justification

We follow the formal definition of a limit to justify the above rules.
Assume that $\lim_{n \rightarrow \infty} f(n) / g(n) = 0$.
Then for any $\epsilon > 0$, there exists an $n_0 > 0$ such that,
$|f(n) / g(n) - 0| < \epsilon$ for all $n \geq n_0$.
In particular, we have
$f(n)/g(n) < \epsilon$ for all $n \geq n_0$.
The above inequality holds for an $\epsilon > 0$, so we set $\epsilon$ to a constant $c > 0$.