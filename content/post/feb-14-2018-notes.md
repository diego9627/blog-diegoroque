---
title: "Feb 14 2018 Notes"
date: 2018-02-14T09:02:38-05:00
draft: true
tags: ["18.S996","18.702"]
---

# 18.S996

## DeGroot Convergence

Note DeGroot model assumes ergodic. Note that if \\(\pi\\) is the stationary solution,
 \\(\pi(i)\\) is the centrality of \\(i\\). This is just PageRank.

Rate of convergence: \\(|s(i,t) - E\_{\pi} s| = |Es(X(i,t)) - E\_{\pi}s| \leq 2|P(i,t)-\pi|_1\\).

Other techniques in MC include:

* Spectral techniques and conductance
* Coupling
* Log Sobolev inequalities

The \\(\epsilon\\)-mixing time of W is 

$$\min\\{t : \max_i |P(i,t) - \pi|\_{TV} \leq \epsilon\\}$$

We also have roughly that mixing time of \\(W\\) iff convergence of Degroot Model.

EG: At \\(\epsilon\\) mixing time \\(t\\) for \\(i\\): \\(|s(i,t) - E\_{\pi} s|\leq \epsilon\\)

Main difference of Markov and Degroot: multiplying right vs left.

## Condoctance bounds

For set \\(A\\):

$$\pi(A) = \sum\_{x\in A}\pi(x)$$
$$\pi(\delta A) = \sum\_{(x,y)\in A\times A^c} w(x,y)\pi(x) + w(y,x)\pi(y)$$

Def Conducatance: $$I = \min\_{\pi(A) \leq \frac{1}{2}} \frac{\pi(\delta A)}{\pi(A)}$$

Big conductance = connected society.

Roughly theorem: **If there are no isolated communities, then convergence is quick.**

If \\(t\geq \frac{8\alpha}{I^2} (1 + \max \ln \frac{1}{\pi(i)})\\)
then $$|P(i,t) -\pi|\_{TV} \leq \exp(-\alpha) $$ thus 
$$ |s(i,t) - E\_{\pi}s| \leq \exp(-\alpha) $$

## Cheating in DeGroot

Can somebody cheat and convince everybody?

Claim: If the cheater always says that value and the chain is ergodic, the opinions will 
converge to the cheater. 

Proofish: Every walk eventually hits the cheater, so it must return that value.

Proofish2: Harmonic functions on graphs. Limiting value is harmonic, 
so \\(s(i) = \sum_j W(j,i) s(j)\\) for the solution and only solution is everything 
equal to cheater's value. (Exercises)

(Check Perron Frobenius, but not that's not actual solution)

## The Voter Model

Repeated *sampling* of opinions of neighbors. 

Similar setup. \\(n\\) individuals. Initial signals \\(\pm 1\\), with certain correctness
probability.  Different update rule: \\(P[V(i,t+1) = V(j,t)] = w(i,j)\\). 
So you copy an opinion with certain probability. 

Several variants: We will talk about in parallel, synchronous. Another, not talked here,
is edges ring according to Poisson clocks, asynchronous.

Take \\(V(i,t)\\) for voter model, \\(s(i,t)\\) for DeGroot.

Similar to DeGroot: The expected result of this process is the result of DeGroot.
This by induction and linearlity of expectation.

$$ E[V(i,t)] = s(i,t) $$

Claim: If \\(W\\) is ergodic, all the values will end up the same.
Proofish: All + and - are absorbing states. For any other state, there exist a sequence 
from that to one of those two absorbing states.

Claim: There is no learning in this model, regardless of graph.
Proofish of cycle: Suppose every gets correct signal \\(1-10^{-10}\\).

$$P[value = -1]=P[\lim V(i,t) = -1] = \lim s(i,t) = \sum \pi(i)s(i) = 10^{-10}$$

hence there's a probability \\(P[all\, wrong]\geq 10^{-10}\\). So convergence but no learning.

General: Assume self loops and strongly connected. If every signal between \\(p\\) and \\(q\\),
then final probability between \\(p\\) and \\(q\\).

## Convergence Rate of Voter

Coalescence arguments. Martingale arguments.
See Liggett, Durrett.

Wald's first equation: If \\(M\\) is a martingale and \\(T\\) is stoping time,
then \\(E[M(T)] = E[M(0)]\\) (this will be used in exercise).
Second: Under some conditions, lower bound for \\(Var[M(T)]\\).

Claim : V(i,t) is voter. Exercise: Proof V(i,t) is a martingale.
Exercise 2: Bound convergence tim ein O(|V|^2). Get better bounds when the graph expands.

# 18.702 (Class)

Masche's Theory: The category of linear G-representations is semi-simple.

Semisimple rougly means being able to decompose into simple objects, so without subobjects.

Remark: This is kinda useless because it's nonconstructive, and doesn't tell you anything 
about how to go about it.
Even in the abelian case, we needed to find a simultaneous eigenbasis which is hard.
So a lot of this is problem about **basis**.

There are two natural basis independent quantities for any \\(T: W\to W\\).
These are the determinant (product of eigenvalues) and the trace (sum of eigenvalues).
We will focus on the trace. 

Let \\(\rho : G\to GL(W)\\) be a representation. The character of that representation 
is \\(\chi\_{\rho} : G\to \mathbb{C}\\), that sends \\(g\mapsto \text{trace }\rho(g)\\).
Characters are constant on conjugancy classes. 

This because if we have \\(g, hgh^{-1}\\), their representations are 
\\(\rho(g),\rho(h)\rho(g)\rho(h)^{-1}\\). From this we can conclude because 
\\(\text{trace }AB =\text{trace }BA\\) or because trace is base independent (thinking of
\\(\rho(h)\\) as a base change).

If \\(g\\) has order \\(k\\), then all eigenvalues \\(\rho(g)\\) are roots of \\(k\\)-th unity.
Then trace is sum of roots of unity.

We have \\(\chi(g) = \overline{\chi(g^{-1})}\\), since eigenvalues of inverses are inverses 
of eigenvalues, we add, and they are roots of unity. Conclude.

If \\(\chi_i\\) are characters, then \\(\sum_i \chi_i\\) is a character.

Characters have two good things:

* We can pick an element in a conjugacy class and compute their character
* We can choose bases tailored to a particular group element.

Define inner product on characters. Define 

$$ \langle\chi_1,\chi_2\rangle = \frac{1}{|G|}\sum_g \overline{\chi_1(g)}\chi_2(g) $$

This is an inner product on the vector space spanned by the irreducible characters. 
This is mathematically correct but basically ad-hoc.

Define a class function on \\(G\\) any function that is constant on conjugacy classes.
The set of all class functions is a finite dimensional complex vector space with dimension 
equal to the number of classes.

Theory (of characters)

* Irreducible characters are orthonormal according to that dot product
* There are as many irreducible characters as conjugancy classes
* If \\(\rho_i\\) are the irreducible representations, with \\(dim \rho_i = d_i\\)
then \\(d_k| |G| = \sum_i d_i^2\\).

# MIT Categories Seminar

Comments from the [website](http://localhost:1313/post/feb-14-2018-notes/):


* Often what can be considered the meaning of a sentence involves filling in implicit 
information. 
* [Expressing 'The Structure of' in Homotopy Type Theory](https://ncatlab.org/davidcorfield/files/AndTalk2.pdf)
* [lexicalism and pushback](https://golem.ph.utexas.edu/category/2018/02/linguistics_using_category_the.html#c053532)
* Foreign speakers can be parsed to correctness
* Words are *very* flexible
* meaning eliminativism/relevance theory

Mine:

* This paper seems useless
* Introducing more and more mathematics to the problem of languages seems like epicycles and deferents
* RNN are doing great at translating
