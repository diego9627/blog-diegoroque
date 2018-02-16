---
title: "Feb 15 2018 Notes"
date: 2018-02-15T08:29:11-05:00
draft: false
tags: ["OptUROP","18.408", "MITCT", "AIMathUROP", "DRP"]
---

# OptUROP

Trying to remember wtf did I coded

# 18.408

## Clustering

We want to partition the graph into two essential parts. Let \\(S\\)
be the number of vertices, \\(\overline{S}\\) the complement, \\(e(S)\\) the edges 
betwteen \\(S\\) and \\(\overline{S}\\).

Bad answers:

* Mincut, minimize \\(e(S)\\)
* Approximate Bisection (we should be able to cut small pieces)

Some Better answers:

* Define the cut ratio $$ \phi(S) = \frac{e(S)}{\min(|S|,|\overline{S}|)} $$,
and this is the min cut ratio
* Alternatively, weight by degree. Define \\(\deg(S) = \sum_v \deg(v)\\),
and define $$ \Phi(S) = \frac{e(S)}{\min(d(S), d(\overline{S})) } $$ 
* Second kind of makes more sense. The objects oyu actually want to deal with are the edges.
* Sadly, solving this is NP-Hard

## Integer program for Cut Ratio

Think of a cut as \\(x\in \\{-1,+1\\}^n\\), where \\(x_i = S\Leftrightarrow i\in S\\).

Thus \\(e(S) = \frac{1}{4}\sum\_{(i,j)\in E}(x_i-x_j)^2\\).

We also have \\(|S||\overline{S}| = \sum\_{i,j} [i\in S][j\in \overline{S}]
=\frac{1}{2}\sum\_{i,j} [x_i \neq x_j] = \frac{1}{4} = \sum\_{i<j} (x_i - x_j)^2 \\).

We have \\(\frac{n}{2}\min(|S|,|\overline{S}|) \leq |S||\overline{S}|\leq n\min(|S|,|\overline{S}|)\\)

Now, after removing the constraint, we can solve this. Since this is homogeneous, we can 
make \\(x\in [-1,1]^n\\) if that's more comfortable.

## Interlude on relaxations

* You have "Minimize \\(f(x)\\) subject to \\(x\in C\\). But this is hard. So just minimize 
\\(f(x)\\), or \\(f(x)\\) over \\(C^{\prime}\supset C\\) an easier constraint
* This gives a lower minimum \\(q\\). This is probably not the thing you want, but it outside.
* After this, you round \\(q\in C^{\prime}\\) to \\(q^{\prime}\in C\\). 
* To show this givevs an approximation prove \\(f(q^{\prime})\leq \gamma f(q)\\).
* After this, you get \\(f(q^{\prime})\leq \gamma f(q) \leq \gamma f(p) \leq \gamma f(q^{\prime})\\)
* So this gives you \\(\gamma\\)-approximations.

## Our case

Since the ratio is shift and scale invariant, we can assume \\(\sum_i x_i = 0\\).
Thus it's ortogonal to n-vector, and since we are looking at the laplacian, then 

$$ \sum\_{i<j} (x_i -x_j)^2 = n\sum_i x_i^2 $$

Now after this substitution, we get we want to minimize

$$ \min\_{x\in \mathbb{R}^n,\sum_i x_i = 0} \frac{\sum\_{(i,j)\in E} (x_i -x_j)^2}{n\sum_i x_i^2} =\frac{\lambda_2}{n}$$

Thus

 $$ \phi(G) = \min_{S\subset V} \frac{e(S)}{\min(|S|,|\overline{S}|)} \geq \ldots\geq \frac{\lambda_2}{2} $$

To prove tightness, Cheeger's inequality! (again! second)

We get 
$$ \frac{\phi(G)}{2d\_{\max}} \leq \lambda_2 \leq \phi(G) $$

This is tight, but it is essentially because we are considering the wrong quantity. We now 
consider \\(\Phi(G)\\). We will consider this on the normalized laplacian 
\\(N = D^{\frac{-1}{2}}LD^{\frac{1}{2}}\\).
Cheeger inequality for this says 
$$ \frac{\Phi(G)^2}{2} \leq \mu_2 \leq 2\Phi(G) $$
where \\(\mu_i\\) are the eigenvalues of \\(N\\).

## Getting a cut from (almost) any vector

Suppose you have \\(y\in \mathbb{R}^d\\) perpendicular to the diagonal vector. We will
order the coordinates, then partition according to a certain threshold, with lower on one side,
and higher on the other.

End up proving that anything vert close to \\(I\\) is good enough.

# MITCT

Reading the paper. David Spivak agreed it was stupid. Next paper looks more interesting.

# AIMathUROP

Submitted urop. Will start reading [this](https://arxiv.org/pdf/1701.06972.pdf)
and watching [this](https://arxiv.org/pdf/1701.06972.pdf).

* Deep Network Guided Proofs
* DeepMath
* A Fully Automatic Theorem Prover with Human-Style Output

# DRP

Solved some problems from DRP.