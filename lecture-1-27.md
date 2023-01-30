# Lecture 5 (1-27)

## o-Notation

For a given function g(n), let o(g(n)) denote the following set of functions:

$$o(g(n)) = \{f(n) : 0 \leq f(n) \leq cg(n) \text{ for all n } \geq n_0 \text{ for some positive constants c and } n_0 \}$$

The function g(n) is an upper bound that is not asymptotically tight for $f(n)$.

### Example 1

Show that $f(n) = 8n^2-210n+330$ is in $o(n^3)$.

In this example, $g(n) = n^3$.

$$8n^2 - 210n + 330 \leq 8n^2 330n - 330 = 9n^2 - n^2 - 330$$

For any positive constant $c > 0$, we need to find a positive contant $n_0$ such that:

$9n^2 < cn^3$ or $9 < cn$ or $\frac{9}{c} < n$ for all $n \geq n_0$

Choosing $n_0$ to be an integer larger than each of 330 and $\frac{9}{c}$, we have
$8n^2-210+330 \leq 9n^2 < cn^3$ for all $n \geq n_0$.
So $8n^2 -210n + 330 \in o(n^3)$.

### Example 2

Show that $9n^2$ is not in $o(n^2)$.

We use proof by contradiction. Assume that $9n^2$ is in $o(n^2).

Then for any positive constant $c>0$ there exists a positive constant $n_0$ such that

$9n^2 \leq cn^2$

### Example 2

Show that $9n^2$ is not in $o(n^2)$.

We use proof by contradiction. Assume that $9n^2$ is in $o(n^2).

Then for any positive constant $c>0$ there exists a positive constant $n_0$ such that

$9n^2 \leq cn^2$ for all $n \geq n_0$.

Dividing both sides by $n^2$ gives

$9 < c$, which is false if we choose $c=8$.
This contradiction results from the assumption that $9n^2$ is $o(n^2)$

Thus, $9n^2$ is not in $o(n^2)$.

## $\omega$-Notation

For a given function $g(n)$, let $\omega(g(n))$ denote the following set of functions:

$\omega(g(n)) = \{f(n) : 0 \leq cg(n) \leq f(n) \text{ for all n } \geq n_0 \text{ for some positive constants c and } n_0 \}$

The function $g(n)$ is a lower bound that is not asymptotically tight for $f(n)$.

We can show that $f(n) = 8n^2 - 210n + 330$ is in $\omega(n)$, but $9n^2$ is not in $\omega(n^2)$.

The relationship between $\omega$-notation and o-noation

## Monotonicity

A function $f(n)$ is monotonically increasing if $f(n) \leq f(n)$ for all $m \leq n$.
For example, $f(n) = 2$ is monotonically increasing.

Let $d$ be a positive constant.
It can be shown by mathematical induction that the function $T(n)$ defined below is monotonically increasing:

$T(1) = d$

$T(n) = T(\lceil \frac{n}{2} \rceil) + T(\lfloor \frac{n}{2} \rfloor) + dn$ for $n > 1$

A function $f(n) is strictly increasing if $f(m) > f(n)$ for all $m < n$.
For example, $f(n) = n + 2$ is stictly increasing.

A function $f(n) is monotonically decreasing if $f(n) \geq f(n)$ for all $m \leq n$.

A function $f(n) is strictly deceilreasing if $f(m) > f(n)$ for all $m < n$.

## Floors and Ceilings

For any real number x, let $\lfloor x \rfloor$ denote the largest integer less than or equal to x, and let $\lceil x \rceil$ denote the smallest integer greater than or equal to x.
For example, $\lfloor 5 + \frac{1}{3} \rfloor = 5$ and $\lceil 5 + \frac{1}{3} \rceil = 6$.

The inequality $\lfloor x \rfloor \leq x \leq \lceil x \rceil$ is always true.

Define $k = \lfloor x \rfloor$.
Then $k = x + s$ for real number s with $0 \leq s < 1$.

Then $k = \lfloor x \rfloor$. Then $x = k + s$ for real number $s$ with $0 \leq s < 1$.

Then $x - 1 = k + s - 1 < k = \lfloor x \rfloor$, and

$\lceil x \rceil = k + 1 \leq k + 1 + s = x + 1$ if $s > 0$, or
$\lceil x \rceil = k <  k + 1 = x + 1$ if $s = 0$\lceil x \rceil = k <  k + 1 = x + 1$ if $s = 0$.

For any integer $n$, we have $\lceil \frac{n}{2} \rceil + \lfloor \frac{n}{2} \rfloor = n$.

So if n is even, then $\lceil \frac{n}{2} \rceil + \lfloor \frac{n}{2} \rfloor = \frac{n}{2} + \frac{n}{2} = n$.

If n is odd, i.e. $n = 2k + 1$ for some $k$, then $\lceil \frac{n}{2} \rceil + \lfloor \frac{n}{2} \rfloor = (\frac{n}{2} + 1)  + \frac{n}{2} = n$.

## Modular Arithmetic

For any integer a and any positive integer n, the value of the operation $a$ mod $n$ is the remainder of the quotient of $\frac{a}{n}$.

$a$ mod $n = a - n \lfloor \frac{a}{n} \rfloor$

It follows from the definition that $0 \leq a$ mod $n < n$.

If (a mod n) = (b mod n), then a is equivalent to b modulo n: a $\equiv$ b (mod n).

In other words, $a \equiv b$ (mod n) if and only if n divides $b - a$ exactly.

## Polynomials

For a nonnegative integer $d$, a polynomial in n of degree d is a function p(n) of the form

$p(n) = \Sigma_{i=0}^d a_i n^i$

where the constants $a_0, a_1,...,a_d$ are the coefficients of the polynomial with $a_d \neq 0$.

If $a_d > 0$, then the poly nomial $p(n)$ is asyptotically positive.

## Exponentials

For any rela number $a > 0$ and any integers $m$ and $n$, then the following identities hold:

$a^0 = 1$

$a^1 = a$

$a^{-1} = \frac{1}{a}$

$(a^m)^n = a^{mn} = (a^n)^m$

$a^m a^n = a^{m+n}$

For any real number x, the exponential function $e^x$ is of the following form

$e^x = 1 + x + \frac{x^2}{2!} + \frac{x^3}{3!} + ...$

where the exclamation mark denotes the factorial function.

## Logarithms

The following notations are used in the analysis of the algorithms:

$lg(n) = log_2n$ (binary logarithm)

$ln(n) = log_en$ (natural logarithm)

$lg^k(n) = (log_n)^k$ (exponentiation)

$lglgn = lg(lg(n))$ (composition)

An important notational convention: $lgn + k = (lgn) + k$, not $lg(n+k)$.

The logarithmic function to base a is the inverse of hte exponential function with base a.

If $a^x = y$, then $x = log_ay$ (e.g. $2^4 = 16$ and $4 = log_216$)

That is, applying the exponential function then the logarithmic function with the same base gives us back the original value:

$x = log_ay = log_a(a^x)$ (1)

And applying the logarithmic function then the exponential function with the same base alos gives us back the original value:

$y = a^x = a^{log_ay}$ (2)

We can use these identities and some identities about exponentia functions to get other useful identities.

For example, we start with the following identity.

$ab = (a)(b)$

Apply (2) to $ab$ on the left side, and (2) to $a$ and $b$ separately on the right side, we obtaino

$c^{log_c(ab)} = (c^{log_ca})(c^{log_cb})$

Applying the identity about the exponential function on the right side we get

$c^{log_c(ab)} = c^{log_ca + log_cb}$

Applying the ogarithmic function with base c to each side, we obtain

$log_cc^{log_c(ab)} = log_cc^{log_ca + log_cb}$

Then applying (1) to each side we obtain

$log_C(ab) = log_c(a) + log_c(b)$

For real numbers $a > 0$, $b > 0$ and $c > 0$, we have

$a = b^{log_ba}$

$log_c(ab) = log_c(a) + log_c(b)$

$log_ba^n = nlog_ba$

TBD