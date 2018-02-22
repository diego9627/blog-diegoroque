---
title: "Feb 21 2018 Notes"
date: 2018-02-21T09:35:48-05:00
draft: false
tags: ["18.S996", "18.702", "TODO"]
---

# 18.S996

## Bayesian (learning) newtorks?

Previously we were assuming they behaved in a certain manner. In a certain way, we assumed they 
are kind of dumb. Nnow we will assume they aren't.

So we can apply bayes rules, and given all the signals, get the actual probability of being
correct. 

Setup: 

* \\(S\in \\{0,1\\}\\), with \\(P[S = 1]=\frac{1}{2}\\). 
* Distributions of signals  \\(D_0, D_1\\). Note that we are not assuming anymore that it's symmetric. 
* A (directed) *social network* \\(G = (V,E)\\) of size \\(n\\) **with** self-loops

Running:

* At time zero, they get a signal \\(X(i,0)\\) from \\(D_S\\)
* Let \\(F(i,0) = \sigma(X(i))\\)
* \\(F(i,t) = \sigma(F(i,t-1),X(j,t), i\to j \in E)\\)
* At time \\(t\\), agent \\(i\\) declares \\(X(i,t)= P[S=1|F(i,t-1)] = E[S|F(i,t-1)]\\).
That is, at time zero they say their probability. At time 1, they see all the things they learned
from neighbors, compute their new probability with that information, and they declare their 
new information. At time 2, and so on and so on and so on.
* Note at step two they do the learning according to the graph


Key assumption: Agents know \\(G,D_0,D_1\\).

This is annyoing bc they are smart as we are.

Normal questions: Do they converge? What do they converge? Do they learn?

## Agreement

Looking at one agent: We get that \\(X(i,t)\\) is a martingale, because at any point it
has more information. It's bounded, and bounded martingales converge.

Looking at everything: If the graph is not strongly connected, not everybody has access to
all the information. So we need strong connectivity. If \\(G\\) is strongly connected, 
we have \\(\lVert X(i)-S)\rVert-2^2 = \lVert X(j) - S\rVert_2^2\\).

Proof: We have that if \\(i\\) observes \\(j\\), then \\(X(j)\in F(i)) by a limiting argument.
Conditional minimizes L2 norm, so  \\(\lVert X(i)-S)\rVert-2^2 \leq \lVert X(j) - S\rVert_2^2\\).
Since it's strongly connected, anything is less than anything, so all tare equal.

Rest of proof: If not all equal, then there are two adjacent that are not equal, say \\(i,j\\).
Take \\(Z =\frac{X(i)+X(j)}{2}\\), which is in \\(F(i)\\). By convexity, we have that 
\\(\lVert X(i)-S)\rVert-2^2 = \lVert X(j) - S\rVert_2^2 > \lVert Z - S\rVert \\).
But this is a contradiction, since \\(Z\in F(i)\\). Hence they must be all equal.

So they all converge to the same value.

TODO: Check "Conditional is minimizer of L2" and "Martingales"

Note that we didn't assume signals were independent! So this model always converge.
In a sense, it's a critique of bayesian economics, since this means that there's *always*
convergence, but people in the real world agree to disagree.

## Learning

Assume \\(G\\) is strongly connected. If not independent, they might not converge.
If the signals are i.i.d., then everybody converges to the actual posterior from seeing 
everything. The statements/proof works whenever the posterior beliefs are common knowledge.

Let 

$$ Z_i = \log \frac{\mathbb{P}[S = 1 | X(i)]}{\mathbb{P}[S = 0|X(i)]} = 
\log \frac{\mathbb{P}[X(i)|S = 1]}{\mathbb{P}[X(i) | S = 0]}, Z = \sum_i Z_i$$

so \\(\mathbb{P}[S = 1|X(1),\ldots, X(n)] =L(Z)\\), where \\(L(x) = \frac{e^x}{e^x+1}\\).

Claim: Since \\(X\\) is \\(\mathcal{F}_i\\)-measurable

$$ X = \mathbb{E}[L(Z)|\mathcal{F}_i] = \mathbb{E}[L(Z) | X] $$

Since \\(Z_i\\) is \\(\mathcal{F}_i\\)-measurable, we have 

$$ \mathbb{E}[Z_i\cdot L(Z) | X] = \mathbb{E}[\mathbb{E}[Z_i\cdot L(Z)|\mathcal{F}_i]|X] 
=\mathbb{E}[Z_i\cdot X | X] = \mathbb{E}[Z_i|X]\mathbb{E}[L(Z)|X]
$$

In particular, \\(\mathbb{E}[Z\cdot L(Z)|X] = \mathbb{E}[Z|X]\mathbb{E}[L(Z)|X]\\). 
Conditional on \\(X\\), by Chevychev's, it should be a strict inequality if they were 
not constant. But since they are equal, we have that \\(Z,L(Z)\\) are constant.
Hence \\(L(Z)\\) is a function of \\(X\\). This can be computed in each \\(\mathcal{F}_i\\).

Open problems:

1. Is learning valid under weaker cnoditions?
2. How quick is the convergence to the agreed value?
3. Are there good algorithms to compute the dynamics?

We will look at 2 and 3 later.

# 18.702

Class hada

# Categorical Logic

TODO
