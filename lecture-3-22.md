# Lecture 3-22

#### Proof

We use induction on the number of queue operations.

The basis of the induction is the situation where after the source vertex $s$ is removed from $Q$, a vertex $v$ is enqueued during the search from $s$.
In this case $v.d = 1 \geq 0 = s.d$ and $v.d = 1 \leq 0 + 1 = s.d + 1$.
Thus, the lemma holds.

For the inductive step, we show that the lemma holds after both dequeuing and enqueuing a vertex.

If $r \geq 2$ and the head $v_1$ of the queue is dequeued, $v_2$ becomes a new head, and $v_1$ is the last vertex removed from the queue.
Let $u$ be the last vertex removed before $v_1$ is dequeued.
By the inductive hypothesis, $v_r.d \leq u.d + 1, u.d \leq v_1.d$, and $v_1.d \leq v_2.d$.
Moreover, $v_r.d \leq u.d + 1 \leq v_1.d + 1, v_1.d \leq v_2.d$, and the remaining inequalities are unaffected.
Thus, the lemma holds.

Now consider the case where vertex $v$ is enqueued in line 17 of BFS.
In this case, vertex $v$ is discovered during the search from a vertex $u$, which was the last vertex removed from the queue.
Thus, we have $v.d = u.d + 1$.

If the queue was empty before $v$ is enqueued, then $u.d \leq u.d + 1 = v.d$ and $v.d \leq u.d + 1$.
Thus, the lemma holds.

If the queue contains the vertices $<v_1, v_2, ... v_3>$ with $r \geq 1$ before $v$ is enqueued, then by inductive hypothesis, $u.d \leq v_1.d$ and $v_r,d \leq u.d + 1$.
Moreover, $v_{r+1}.d = v.d \leq u.d + 1$, $u.d \leq v_1.d$, $v_r.d \leq u.d + 1 = v.d = v_{r+1}.d$, and the remaining inequalities are unaffected.
Thus, the lemma holds.

### Theorem 22.5

Let $G = (V,E)$ be a directed or undirected graph, and suppose that BFS is run on G from a given source vertex $s \in V$.
Then, during its execution, BFS discovers every vertex $v \in V$ that is reachable from the source $s$, and upon termination, $v.d = \delta(s,v)$.

TBC

#### Proof

We use proof by contradiction.
Assume that some vertex recieves a d value not equal to its shortest path distance.

Let $v$ be the vertex with a minimum $\delta(s, v)$ that receives such an incorrect $d$ value, $v$ cannot be $s$.

By Lemma 22.2, $v.d \geq \delta(s,v)$, and thus we conclude that $v.d > \delta(s,v)$.

Let u be the vertex immediately preceding $v$ on a shortest path from $s$ to $v$, so that $\delta(s,v) = \delta(s,u) + 1$.

Because $\delta(s,u) < \delta(d,v)$, and because of how we choose $v$, we have $u.d = \delta(s,u)$.

It follows from these properties that $v.d > \delta(s,v) = \delta(s,u) + 1 = u.d + 1$.

Consider the time when BFS chooses to dequeue vertex u from Q in line 11.
At this time, vertex v is either white, gray, or black.
We show that in each of these cases, we obtain a contradiction to inequality (22.1).

If $v$ is white, then line 15 sets $v.d = u.d + 1$, contradiction inequality (22.1).

If $v$ is black, then it was already removed from the queue.
By Corollary 22.4, $v.d \leq u.d$, contradiction inequality (22.1).

If $v$ is gray, then it was painted gray upon dequeing some vertex $w$, which was removed from $Q$ earlier than $u$ and for which $v.d = w.d + 1$.

However, by Corollary 22.4, $w.d \leq u.d$, and so we have $v.d = w.d + 1 \leq u.d + 1$, once again inequality (22.1).