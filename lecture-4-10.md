# Lecture 4-10

For the HW - prove by induction

## Overview of NP-Completeness

The worst-case running time of a polynomial-time algorithm on inputs size n is $O(n^k)$ for some constant $k$.

All algorithms we have studied so far in this course are polynomial-time algorithms.

There are problems that cannot be solved by any computer, no matter how much time is allowed.

For example, Halting Problem is to determine, given a program and input to the program, whether the program will eventually halt when run with that input.
This problem cannot be solved by any computer.

The time hierarchy theorems say that no matter how hard a problem is, there are always harder problems.
For example, there are problems that can be solved in exponential time, but not in polynomial time.

We study three classes of problems: P, NP, and NPC (NP-complete problems).

Informally, the class P consists of those problems that are solvable in polynomial time.

All the problems we have studied so far are in P.

Informally, the class NP consists of those problems that are 'verifiable' in polynomial time.

If we are somehow given a 'certificate' of a solution, then we could verify that the certificate is correct in polynomial time.

For example, a Hamiltonian cycle of a directed graph $G = (V,E)$ is a simple cycle that contains each vertex in $V$.

The Hamiltonian-cycle problem is to determine whether the directed graph $G$ contains a Hamiltonian cycle.

For this problem a certificate would be a sequence $<v_1, v_2, \ldots, v_n>$ of $|V|$ vertices.
We could check in polynomial time that (v_i, v_{i+1}) is in $E$ for $i = 1, 2, 3, ... |V| - 1$ and that (v_{|V|}, v_1) is in E as well.

Thus, the hamiltonian-cycle is in NP.

Any problem in P is also in NP, since any problem in P can be solved in polynomial time without even being given a certificate.

The open question is whether $P$ is a proper subset of NP.

Informally, a problem is NP-complete if it is in NP and is as 'hard' as any problem in NP.
This means that if any NP-complete problem can be solved in polynomial time, then every problem in NP can be solved in polynomial time.

The class NPC consists of those problems that are NP-complete.

We will learn that the Hamiltonian cycle problem is NP-complete.

Hundreds of NP-complete problems have been studied to date, but no polynomial-time algorithm has been discovered for any of them.

As a computer scientist, you need to understand the concept of NP-completeness.

If a problem is NP-complete, you would do better to design an approximation algorithm, instead of an algorithm that solves the problem exactly.