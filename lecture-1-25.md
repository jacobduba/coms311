# Lecture 4 (1-25)

## Asymptotic Efficiency

The asymptotic efficiency of algorithms is concerned with how th running time of an algorithm increases with the input size tending towards infinity (increaseing without bound).

An algorithm that is asymptotically more efficient will be the best for all but small inputs.

The asymptotic running time of an algorithm is described in terms of functions whose domians are the set of natural numbers $\mathbb{N} = \{0, 1, 2, 3...,\}$.

We assume that every function in every asymptotic notation is asymptotically negative.

## O-Notation

For a function $g(n)$, let $O(g(n))$ denote the following set of functions.

$$O(g(n)) = \{f(n) : 0 \leq f(n) \leq cg(n) \text{ for all n } \geq n_0 \text{ for some positive constants c and } n_0 \}$$

**TBD**

### Example 1

Show that $f(n) = 5n^2 + 30n + 70$ is in $O(n^2)$.

We know that 

$70 \leq 70n$ if $n \geq 1$, and $30n + 70n = 100n \leq 100n^2$ if $n \geq 1$.

By using these two inequalities for all $n \geq 1$, we obtain

$$f(n) = 5n^2 + 30n + 70 \leq 5n^2 + 100n \leq 5n^2 + 100n^2 = 105n^2$$

Setting $n_0 = 1$, and $c = 105$ we have

$f(n) \leq cn^2$ for all **TBD**

### Example 1 (Another way)

Setting $n_0 = 70$ anf for all $n \geq n_0$, we have

$$f(n) = 5n^2 + 30n + 70 \leq 5n^2 + 30n + n = 5n^2 + 31n \leq 5n^2 + n^2 = 6n^2$$

So for $n_0 = 70$ and $c_1=6$ we have 

$f(n) \leq c_1n^2$ for all $n \geq n_0$. So f(n) is in $O(n^2)$, where $g(n) = n^2.

Note that for n_0 = 0 

**TBD** 

### Example 2

Show that $f(n) = 3n - 100$ is not in $O(1)$, where $g(n) = 1$.

We use proof by contradiction.
Assume that $f(n) = 3n - 100$ is in $O(1)$.

Then there exists a positive constant $c$ and a positive integer $n_0$ such that

$3n - 100 \leq c * 1 = c$ for all $n \geq n_0$.

Moving the term 100 to the right side, and dividing each side by 3, we have $n \leq (c + 100)/4$ for all $n \geq n_0$.

This is false when we set $n$ to an integer larger than each of $n_0$ and $(c + 100) / 3$ for all $n \geq n_0$

This is false when we set $n$ to an integer larger than each of $n_0$ and $(d + 100)/3$

The contradiction results from the assumption that $f(n) = 3n - 100$ is in $O(1)$.

## $\Omega$-Notation

For a function $g(n)$, let $\Omega(g(n))$ denote the following set of functions.

$$ \Omega(g(n)) = \{f(n) : 0 \leq cg(n) \leq f(n) \text{ for all n } \geq n_0 \text{ for some positive constants c and } n_0 \}$$

**TBD**

### Example

Show that $f(n) = 5n^2 -130n -450$ is in $\Omega(n^2)$.
In this example, $g(n) = n^2$.
Evauate $f(n)$ at 1 and 1,000,000.

We need to show that there exist postiive constants $c$ and $n_0$ such that
$5n^2 - 130n - 450 \geq c * n^2$ for all $n \geq n_0$.

We choose a larger value for n_0, say, $n_0 = 450$ so that we can drop the two terms of the lower order.

$$5n^2 - 130n - 450 = 5n^2 - 131n + n - 450 \geq $$
$$5n^2 - 131n = 4n^2 + n^2 - 131n = 4n^2 + (n - 131) \geq 4n^2$$

Choosing $c = 4$ and $n_0 = 450$, we have $5n^2 -130n - 450 \geq cn^2$ for all $n \geq n_0$.

## $\Theta$-Notation

For a function $g(n)$, let $\Theta(g(n))$ denote the following set of functions:

$$ \Theta(g(n)) = \{ f(n) : 0 \leq c_1 * g(n) \leq f(n) \leq c_2 * g(n) \text{ for all n } \geq n_0 $$
$$\text{ for some positive constants $c_1$, $c_2$ and } n_0 \}$$

In other words, for all $n \geq n_0$, $f(n)$ is in $O(g(n))$ and in $\Omega(g(n))$.

**TBD**

### Example

Show that $f(n) = 8n^2 - 210n - 330$ is in $\Theta(n^2)$.

We choose a large value for $n_0$, say, $n_0 = 330$ so that we can drop the two terms of the lower order.
For all $n \geq n_0$, we have

$$8n^2 - 210n + 330 \leq 8n^2 + 330 = 9n^2 - n^2 +330 \leq 9n^2 \text{, and}$$

$$8n^2 - 210n - 330 \geq 8n^2 - 210n = 7n^2 - 210n - 330 \geq 7n^2$$

Choosing $c_1 = 7$ and $c_2 = 9$ and $n_0 = 330$, we have $c_1 * n^2 - 210n + 330 \leq c_2*n^2$ for all $n \geq n_0$.

Note that 8n^2 - 210n +330 is in $O(n^2)$, and 8n^2 - 210n - 330 is in $\Omega(n^2)$.

> For any two functions $f(n)$ and $g(n), $f(n)$ is in $\Theta(g(n))$ if and only if $f(n)$ is in $O(g(n))$ and in $\Omega(g(n))$