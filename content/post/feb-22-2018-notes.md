---
title: "Feb 22 2018 Notes"
date: 2018-02-22T14:36:12-05:00
draft: false
tags: ["18.408", "MIT Categories Seminar"]
---

# 18.408

## Cheeger's inequality

We defined conductange \\(\Phi(S) = \frac{e(S)}{\min(d(S),d(S^c))}\\).

Normalized Laplacian: \\(N= D^{\frac{-1}{2}} LD^{\frac{-1}{2}}\\).
with eigenvalues \\(0\leq \mu_1\leq \ldots \leq \mu_n\\).

For \\(x = D^{\frac{1}{2}}y\\), we get \\(\frac{x^TNx}{x^Tx} = \frac{y^TLy}{y^TDy}\\)

Vector corresponding to \\(\mu_1\\) is \\(\mathbf{d}^{\frac{1}{2}} = D^{\frac{1}{2}}\mathbf{1}\\)
, so

$$ \mu_2 = \min\_{x\perp d^{\frac{1}{2}}} \frac{x^TNx^T}{x^Tx}
=\min\_{y\perp d} \frac{y^TLx^T}{y^TDy} $$

Cheeger inequality for \\(N\\) says 

$$ \frac{\Phi^2(G)}{2} \leq \mu_2 \leq 2\Phi(G)$$

The right side is proved by relaxation, in an eqsy way. The left side is harder. 

For the algorithm, we are going to give an algorithm that finds a cut for every 
\\(y\perp \mathbf{d}\\) with

$$  \Phi \leq \sqrt{ 2\frac{y^TLx^T}{y^TDy} }
 \Leftrightarrow \frac{\Phi^2}{2} \leq \frac{y^TLx^T}{y^TDy} $$

Reminder that we think of vectors as function of graph vertices. The proof is basically 
change variable from \\(x\\) to \\(y\\), then normalize to have center zero, then square 
to have a square, then move to have distance \\(1\\) bewteen minimum and maximum.
Take a random cut and you will have what you need. In particular,
\\(\mathbb{E}[\min(d(S_i), d(\overline{S_i}))] = z^TDz\\),
we get \\(\mathbb{E}[e(S_i)] \leq \sqrt{2\rho} z^T D z\\), the second one by linearity 
of expectation then cauchy shwartz.

## Random walks and spectral graph theory

Let \\(p_t(v)\\) denote the probabilty you are at vertex \\(v\\) at time \\(t\\).
That is, \\(P[X(\cdot,t) = v]\\) in the notes of Social Choice.
We can think of this as a vetor in \\(\mathbb{R}^n\\).

If you are at vertex \\(u\\) at time \\(t\\) you go to a neighvor equiprobably.
Or could be weighted. This is basically a matrix \\(W_G\\).
That is, we get \\(p\_{t+1} = Wp\_t\\). 

If ergodic, this will end up at a stationary distribution. That is, at an eigenvector
with eigenvalue \\(1\\). In the case where \\(W\\) represents an unweighted 
matrix, we get \\(\pi(u) = \frac{d(u)}{\sum_v d(v)}\\). This is clearly a probability vector
and stationary. For the stationary, you can either do algebra, or watch that income and outcomes
from each edge is the same in each direction, everything stays the same. Again, you should
think on edges principally, rather than vertices.

Note that you might not converge if it's bipartite or disconnected.

Easy fix: A lazy randomwwalk. At a time \\(t\\), take a random walk with probability half,
take a step with probability half. The weight isn't important actually. 
Essentially, put a (fat/skinny?) self loop. Or a literal normal self loop. 
(Actually, you only need one loop, but you put it everywhere so you get the same stationary
distribution).

Note that \\(W = AD^{-1}\\) isn't symmetric a priory. For the lazy walk, we get 
\\(W' = \frac{1 + W}{2}\\).
But we can normalize \\(W_N = D^{\frac{-1}{2}} W D^{\frac{1}{2}} = D^{\frac{-1}{2}} 
A D^{\frac{-1}{2}}\\).

Claim: \\(W_N, W\\) have the same eigenvalues and related eigenvectors. 

Suppose \\(W_N v = \lambda v\\). Define \\(q = D^{\frac{1}{2}}q\\). Hence 
\\(D^{\frac{-1}{2}}Wq = W_ND^{\frac{1}{2}}qv = \lambda D^{\frac{1}{2}}v\\).
In particular, \\(Wq = \lambda D^{\frac{1}{2}}v = \lambda q\\).

Eigenvalue of \\(W_n\\) are \\(1-\mu_i\\). Reorder them,
and move down to the correct scale. Now we can use laplacian theorems. 

# MIT Categories Seminar

Goal: To prepare for next week aplications to dimension reduction.

Well known: connection between simplicial sets and topological spaces.

Preamble: Graphs are basically just functors from (the category of two objects 
and two parallel arrows from the left object to the right object) to Set.
This is because they carry the same information.

This is categorical modeling 101. We can also give an indexing category for 
reflexive graphs.

These modeling kind of seems like type theory and category theory. Or 
like the way people build categorical groups, or monoids, or etc.
I guess you can do a category embed in a category?  This is all basically just 
doing the construction with sets and functions, then replace the set with a category.

you can also do this for symmetric reflexive graphs. But this ends up being
a subcategory of \\( FinSet^{op} \\). THis brings us to simplicial sets,
and bumps it back to reflexive graphs.