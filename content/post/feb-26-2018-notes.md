---
title: "Feb 26 2018 Notes"
date: 2018-02-26T09:37:47-05:00
draft: false
tags: ["18.S996", "18.702"]
---

# 18.S996

Theorems:

1. Each agent converges (no assumption, dependent signals, any graph)
2. Strongly connected graphs: all converge to same value (even for dependent signals)
3. Strongly connected and (conditionally) independent signal: 
Converge to posterior given all initial information

Question: Speed of convergence?

Open (Theorem 3): Weaker conditions
Open: Algoritmic complexity

# Learning in finite probability spaces

Family 1: Finite probability spaces 

Question: Assume the probability space of the state of the world and the signals is finite.
How long does it take to converge? Does it converge in finite steps?

Each time: \\(\mathcal{F}_i(t) =  \\) sigma algebra of "knowledge" of agent \\(i\\) at time 
\\(t\\).

Claim/Exercise: If \\(\mathcal{F}\_i(t) = \mathcal{F}\_i(t+1) \\) for all \\(i\\), process
converged.

Claim2; \\(\mathcal{F}_i(t)\\) is just a partition of \\(M^n\\)

Claim 3: \\(\mathcal{F}\_i(t+1)\\) is a refinement of \\(\mathcal{F}\_i(t)\\)

Combining them: Converges in \\(nM^n\\) steps. 

(Check sigma algebra and information)

Open: Can this bound be improved?

Example: \\(X\in [n^2]\\) with uniform prior.
Player 1: Gets group \\(i\\) if \\(X\in [(i-1)n + 1, in]\\).
Player 2: Gets set \\(j\\) if \\(X \in [(j - 1)(n+1) + 1, j(n+1)]\\). (Note that \\(j = n\\)
is \\(X\in[n^2,n^2+n]\\) but this is actually \\(X\in \\{n^2\\}\\)).

We want to estimate \\(S = I[X \in \\{1,n+2,2n+3,\ldots, n^2\\} \\).
Assume \\(X=1\\). 

Player 1: Gets \\(P[S] = \frac{1}{n}\\).
Player 2: Gets \\(P[S] = \frac{1}{n+1}\\).

Player 1: In terms of \\(\mathcal{F}_1\\), we learn that \\(X\neq n^2\\).
So we now have \\(F_1\\) is partitioned/refined into \\(\\{[1,n],[n+1,2n],
\ldots [n^2-n+1,n^2-1],[n^2,n^2]\\}\\)

Player 2: Learns that \\(X\not\in [n^2-n+1,n^2-1]\\) but will say \\(\frac{1}{n+1}\\).

Q: How tight are the bounds? 

It reminds of the eye color island problem! We can actually think about this in terms of the 
sigma algebra, kind of.

# The Gaussian model

State of the world is \\(U(-\infty,\infty)\\), "improper prior". The original signals 
are \\(N(\mu = ?,1)\\). Each agent reports estimate of \\(\mu\\).
We consider a connected graph. 

Pretty simple. Best estimator of gaussians is average of gaussians. At time \\(i\\),
we have the signals of \\(i\\) steps away. We average it. Etc.

Guassian case is "easy" since it's all linear algebra.

Claim: \\(X_i(t)\\) is the minimum variacne estimator of \\(\mu\\) in the span of all that 
agent \\(i\\) has observed up to \\(t\\) time.

Claim: Variance decreases with time.

Claim: If \\(X_v(t)\\) or \\(X_u(t)\\), then the dimension of information goes up by one,
when \\(u,v\\) are connected.

\\(L_v(t) = span \\{X_v(0), X_w(s), s\leq t\\}\\).

Speed is \\(\leq n^2\\). Open problem: less than linear on diameter.
Maybe open (Exercise? Project):  If \\(G_1\subset G_2\\), (same vertex set, less edges)
then speed of \\(G_2) is greater or equal to speed of \\(G_1). That is, adding edges makes the
process slower.

# 18.702

A zero divisor is \\(a\neq 0\\) such that there exist \\(b\neq 0\\) such that \\(ab=0\\).

A ring is an integral domain if it contains no zero divisors. That is, if \\(ab = 0\\)
implies \\(a = 0\\) or \\(b=0\\).

Observation: If \\(I \subset \mathbb{Z}\\) is an ideal, then \\(I\\) is principal.

Definition. A ring \\(R\\) is a principal ideal domain if every ideal is principal and 
it's an integral domain.

# PLV Lunch

Showed automation. Concluded that we should leave the untyped version.

# Categorical Logic

TODO. Didn't go.