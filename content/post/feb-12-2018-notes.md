---
title: "Feb 12 2018 Notes"
date: 2018-02-12T08:26:49-05:00
draft: false
tags: ["18.S996", "18.702", "Categorical Logic"]
---

# 18.S996

## Voting

We used the last class the Neyman Pearson Lemma.

Up to now we have fairness and monotonicity. 

Influence of voter \\(i\\) is \\(E_p[f_i]\\).

Theorem (Talagram 94): Let \\(\delta = \max\_{p,i} E_x[f_i]\\) and \\(p < q\\),
then \\(E_p[f](1-E_q[f]) \leq exp(c\ln \delta (q-p))\\),
in particular \\(E_q[correct] \geq 1 - exp(c(q-0.5)\ln\delta)\\)

Theorem (Friedgut-Kalai-96): If \\(f\\) is transitive and monotone, \\(E_p[f]>\epsilon\\)
then  \\(E_q[f]>1-\epsilon\\),  for \\(q = p+c \log(\frac{1}{2\epsilon})/\log n \\)

Theorem (Haggstron, Kalai M04): If \\(n\\) individuals recieve a signal with 
\\(P[X_i=1]\geq p > \frac{1}{2}\\). If \\(e_i(f,P)\leq \epsilon\\),
then \\(P[correct]>1-\frac{\varepsilon}{p-0.5}\\).

## Exercises

* Example/Exercise: Recursive Majority
* \\(Cov[f,X_i] = E[X_if] - E[X_i]E[f] = p(1-p)e_i(f)\\)
* Prove that weighter majorities are only functions that satisfy HaggKalai conclusion

## What to read a bout

* Markov chain
* Neyman pearson
* Ergodic theory 

## Networks

People have beliefs, they can change over time, alter other people. We want to study
agreement (do they eventually agree?) and learning (is the agreement good, for a suitable 
definition of good)?

First we have to set up a model. The simplest one is basically a markov chain.
It's called the DeGroot model. We have n people with certain internal probabilities of an event 
being true. They start independent internally. After each day, they update according to a
weighted average of their neighbors.

That is, if at day \\(t\\) the probability vector is \\(s(t)\\), and the weight matrix is \\(W\\)
, then we have \\(s(t+1) = Ws(t)\\). Thus a markov chain.

If ergodic, then converges. Is strongly conected, then converges to same value. 

To assess correctness, we check a sequence \\((W_n,\pi^n)\\) of transitions and stationary
distributions that increase in size. We have that the aggreed probability converges to \\(1\\)
(the sociaty is "wise") if \\(\limsup \max_i \pi^n_i = 0\\).

# 18.702

We have that if \\(\rho : G\to GL(W)\\) is not irreducible, then there's a subrepresentation 
\\(\sigma : G\to GL(V)\\) by definition. The problem is that there are many vector spaces 
such that \\(W = V \oplus V_1\\), so the decision is not a canonincal one. 

Looking at \\(S_3\\), we realize that the decomposition given is in someway special because we 
can partition it into orthogonal subspaces.

If we were to have a reducible unitary represepntation \\(\rho: G\to U_n\\) with an invariant 
dot product, then we could take the orthogoal space and check that it works nicely.

Now we just note that being unitariy is something of the space, not of the representation.
Essentially we can make anything unitary. So we do it, by constructing a particular inner 
product. We can do this by taking any then averaging. 

Thus we can choose \\(V_1\\) such that it's invariant under \\(\rho\\) and 
\\(W = V\oplus V_1\\). Iterating, we can decompose \\(\rho\\) into irreducible representations.

# CatLog

## Giraud's axioms

Giraud's theorem proves that the following are equivalent:

1. \\(X\simeq Sh(C,J)\\), for some category and site
2. \\(X\hookrightarrow Set^{C^{op}}\\) a fully faithful functor has has a left exact adjoint 
3. \\(X\\) satisfies the Giraud's axioms

In the previous notes, (1) => (2) and (2) => (3) was done. 

To do (3) => (1), you have to first embed \\(X\\) into a presheave category. You could try
doing this by using the yoneda lemma to directly embed \\(X\hookrightarrow Set^{X^{op}}\\)
but \\(X\\) is necessarily large by the axioms. Thus we need to find a smaller category.

Here we use the only thing we can use, the presentability theorem. This way we obtain a set 
(read small) of objects. This not necessarily is closed by finite limits, but we can enlarge
it and get a set of objects whose spanning full subcategory is closed under finite limits.
(since \\(X\\) is closed under limits). Call this category \\(C\\).

Thus \\(C\\) covers every object in \\(X\\) and is closed under finite limits. 
Now we have a place where to sit \\(X\\). We will consider now the category \\(Set^{C^{op}}\\).
We will build a site on it by the notion of covering given in Giraud's. Thus this 
will give a sheave category on \\(C\\). This will end up being equivalent to \\(X\\).

The way to do this is by consider an explicit equivalence. Following the natural thing,
we consider the functor \\(x\mapsto h_x = Hom_X(x,-)\\) the representable functor,
where the functor varies over \\(C\\).

It is possible to prove this is full, faithful, and essentially surjective.
We will end up using the lemma that says that if \\(\\{U_i\to X\\}\\)
is covering, then \\(\coprod_i h\_{U_i} \to h_X\\) is effective to prove these.
This ends up the prove that \\(X\simeq Sh(C )\\).