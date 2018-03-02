---
title: "Mar 1 2018 Notes"
date: 2018-03-01T09:36:58-05:00
draft: true
tags: ["18.175"]
---

# 18.175

Product measure: \\((\Omega_1, A_1, P_1) \times (\Omega_2, A_2, P_2) \\).
This will be equal to \\((\Omega_1 \times \Omega_2, \sigma (A_1\times A_2), P_1\otimes P_2)\\).
We have \\((P_1 \otimes P_2)(A_1\times A_2) = P_1(A_1)\cdot P_2(A_2)\\).


Just do caratheodory theorem, so we have to check sigma additivity of that in \\(A_1\times A_2\\). 

For finite unions 


Definition: \\(n\\) random variables \\(\xi_1,\ldots, \xi_n\\) on \\((\Omega, \mathcal{A},P)\\)
are independent if for any borel \\((B_1,\ldots, B_n)\\), we have 
\\(P(\xi_i \in B_i \forall i) = \prod_i P(x_i\in B_i)\\).

Sets are independent if their indicator functors are.

Corollary: it is enough to take \\(B_i = (-\infty, b_i]\\) to check independence.

$$ F\_{\xi_1,\ldots,\xi_n}(x_1,\ldots, x_n) = P(\xi_1 \leq x_1 ,\ldots , \xi_n \leq x_n) $$ 

Criteria for independence: should factorize.

In general, independence is about factorizaiton. How insightful.

Theorem: X, Y independent, integrable random variables, then \\(E[XY] = E[X]E[Y]\\).

Proof: X, Y are indicator functions, then it works. Both sides are bilinear, hence
we can do the typical measure theory "standard machine".

# 18.408

Will sample from \\(C_k = M_k \cup M\_{k-1}\\), count each set and use this to 
approximate \\(r_k = \frac{|M_k|}{|M\_{k-1}|}\\)

Sample markov chain/random walk from an appropiate graph. Idea: use canonical path to bound 
\\(\Phi\\), the cut, of a graph. 

The graph is the induced graph by "rotating", eliminating, and adding edges.

Canonical paths: For every \\(s\in M_n \cup M\_{n-1}\\), associate a partner \\(s'\in M_n\\).
Essentially go from any to a perfect in the fastest way. If \\(s\\) is perfect, 
\\(s' = s\\). If it has augmented of path 1, add that. If of three, do that change.
We don't need more.

So we can reduce now to only think about movements between perfect matchings.
This induces three types of paths.

Between perfect matching, check symmetric differenece. We get alternating cycles. Just delte one,
move everything, add one. "Unwide" them.

## High level

* If you can sample, you can approximately count. Expnential gaps. Estimate ratios.

## Diameters and eigenvalues

Intuition: Well-connected graphs have big \\(\lambda_2\\).
Intuition: Well-connected graphs have small diameters
So graphs with big \\(\lambda_2\\) should have small diameter.

First bound: Let \\(\delta\\) is diameter of graph. Assume \\(G\\) is \\(d\\)-regular.
Let \\(M = \frac{A}{2d} + \frac{1}{2}\\) be the lazy random walk matrix.
We have that 

Proof: Let \\(u,v\\) be a diameter. Start walk at \\(u\\), think about the probability
\\(p_t(v)\\) of getting into \\(v\\) in \\(t\\) steps. Hence

$$ |p_t(v) - \pi(v)| \leq (1-\lambda)^t \sqrt{\frac{d(v)}{\min_y d(y)} }  = (1-\lambda)^t $$

If \\(p_t(v) > 0\\), then \\(\delta \leq t\\). Taking \\(t = \frac{\ln n}{\gamma}\\).

Somehow chevychev polynomials were mentioned?
"They are surprisingly commonly the answer".

The Chebychev polynomial \\(T_d\\) is a polynomial such that 
\\(\cos(d\theta) = T_d(\cos(\theta))\\). We can easily see (going through complex numbers)
that \\(T_d(x) = 2x T\_{d-1}(x) - T\_{d-2}(x)\\). (or equivalently 
\\(T_d(x) + T\_{d-2}(x) = 2xT\_{d-1}(x)\\)).

Also \\(T_d(x) = \frac{1}{2}(x + \sqrt{x^2-1})^d + \frac{1}{2}(x - \sqrt{x^2-1})^d\\).

"They are the best polynomials (for a lot of approximation questions)"

Assertions: 

* If \\(x\in [-1,1]\\), then \\(T_d(x)\in [-1,1]\\).
* If \\(x\geq 1 + \eta\\) for \\(\eta\geq 0 \\)

$$ T_d(x) \geq \frac{1}{2}(x + \sqrt{x^2-1})^d \geq 
\frac{1}{2}(1+\eta + \sqrt{2\eta +  \eta^2})^d \geq \frac{1}{2}(1 + \sqrt{2\eta})^d $$

Write \\(xT_d(x) = \mathbb{E}T\_{d+y}(x)\\) where \\(y\\) is -1 or +1 equiprobable.
We can make this for \\(k\\) variables: \\(x^kT_d(x) = \mathbb{E}\_{S_k}T\_{d+S_k}\\)
where \\(S_k = \sum\_{i=0}^k y_i\\). Then we can set \\(d = 0\\).

We can ignore big enough chevycheb polynomials because they are very unprobable.
We can do wack stuff. Among other things, we can approximate polynomials with 
polynomials the root of their degree. So we can make things faster.

Define \\(p\_{k,d}(x)\\) to be the restriction of the expresssion only taking polynomials up to 
\\(d\\). Using that chevychev are bounded and that big are too small,
if we set \\(d = \sqrt{2k \log (\frac{1}{\delta})}\\), we can approximate \\(x^k\\) 
with \\(p\_{k,d}(x)\\) with \\(\delta\\) error.


