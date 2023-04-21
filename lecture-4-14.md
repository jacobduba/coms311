# Lecture 4-14

## Reduction from Vertex Cover to Independent Set

Let $V'$ be a vertex cover of size $k$, $V' \subseteq V$.

For each $(u,v) \in E$, at least one of $u$ and $v$ is in $V'$ if and only if at least one of $u$ and $v4...

...

...

## Intractability

We show how to use polynomial-time reductions to prove that no polynomial-time algorithm can exist for a particular problem B.

Assume that we know that no polynomial-time algorithm can exist for a decision problem A.

Also suppose that problem A can be reduced to problem B in polynomial time.

We use proof by contradiction to show that no polynomial-time algorithm can exist for problem B.

Assume that a polynomial-time algorithm exists for problem B.

Then, the three-step procedure solves problem A in polynomial time, a contradiction.

## NP-Completeness

A problem B is NP-complete if the problem B is in NP and every problem in NP is polynomial time reducible to the problem B.

If we can solve problem B in polynomial time, then we can solve every problem in NP in polynomial time by the three-step procedure described above.

## Polynomial Time

We first formalize our notion of polynomial time solvable problems, which are regarded as tractable for philosophical reasons

A first support argument for this view is that the polynomial-time computable problems in real worlds require time in polynomials of low degrees.

A second one is that a problem solvable in polynomial time on one model (such as the serial random-access machine) is also solvable in polynomial time on another (such as the Turing machine).

A third one is that the class of polynomial-time solvable problems is closed under common operations such as set operations, concatenation, and Kleene star.

## A first NP-Complete Problem

We need a first NP-complete problem to prove a different problem NP-complete by reducing the first problem to the new problem.

The first NP-complete problem is the formula satisfiability problem.

## Formula Satisfiability

An instance of the formula satisfiability problem is a boolean formula $\phi$ in conjunctive normal form...

## Formula Satisfiability

A truth assignment for a boolean $\phi$ is a set of values for its variables.

A satisfying assignment for boolean formula is a truth assignment on which it evaluates to 1.

A formula is stated to be satisfiable if it has a satisfying assignment....

...

## Example 1

Consider $\phi(x_1, x_2, x_3) = (x_1 \leftrightarrow x_2) \land \lnot x_3$

Evaluate $\phi(0,0,0) = (0 \leftrightarrow 0) \land \lnot 0 = 1 \land 1 = 1$

Thus, $\phi(0,0,0)$ is a satisfying assignment and is in SAT.

## Example 2

Consider $\phi(x_1, x_2) = ((x_1 \rightarrow x_2) \land (x_1 \rightarrow \lnot x_2)) \land x_1$

Evaluate $\delta(1, 1) = ((1 \rightarrow 1) \land (1 \rightarrow \lnot 1)) \land 1 = 0$

Evaluate $\delta(1, 0) = ((1 \rightarrow 0) \land (1 \rightarrow \lnot 0)) \land 1 = 0$

Note that $\delta(0,0) = 0$ 

Thus, $\delta(x_1, x_2)$ has no satisfying assignment and does not belong to SAT.

## Method for Showing that a Problem is NP-Complete

1. Prove that the problem $B$ is in $NP$.
2. Select a known NP-complete problem $A$.
3. Describe an algorithm computing a function $f$.
4. The function $f$ preserves the answers; the answer on problem A instance is 'yes' if and only if the answer on problem B instance $f(x)$ is also 'yes'.
5. Prove that the algorithm runs in polynomial time.

## 3-CNF Satisfiability

We show that 3-CNF-SAT, a restricted language of boolean formulas, is NP-complete.
The problem is useful in proving other problems NP-complete.

A *literal* in a boolean formula is a variable or its negation.

A boolean formula is in **conjunctive normal form** of **CNF** if it is expressed as an AND of clauses, each of which is the OR of one or more literals.

A boolean formula is in **3-conjunctive normal form** or **3-CNF** if it is in CNF and each clause contains at most three literals...

## Theorem 34.10

3-CNF-SAT is NP-complete.


## Proof

The algorithm for SAT can be used to verify 3-CNF-SAT so 3-CNF-SAT is in NP.

Next, we show that SAT <= p 3-CNF-SAT.

Let $\phi$ be a boolean formula in CNF.

If the formula contains a clause such as the OR of several literals, we use associativity to parenthesize the expression fully so that each operator in the resulting formula has 1 or 2 operands.

....
