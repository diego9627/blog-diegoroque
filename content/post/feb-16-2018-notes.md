---
title: "Feb 16 2018 Notes"
date: 2018-02-16T11:01:58-05:00
draft: false
tags: ["18.702","PLV lunch", "Categorical Logic", "AI Mathematician UROP"]
---

# 18.702 (Class)

## Characters

Main Theorem on characters

* Irreducible characters are an orthonormal basis for class functions
* The number of irreducible representations/characaters is equal to the number 
of conjugacy classes.
* If \\(\rho_i\\) are the irreducible representations, with \\(\dim \rho_i = d_i\\)
then \\(d_k| |G| = \sum_i d_i^2\\).

The main content is the first point. We will use a lemma that's kind of weird
with respect to motivations.

We defined "objects", i.e. \\(G\\) representations. These 
are representations \\(G\to GL(W)\\). THe same thing as a vector space \\(W\\)
as a linear \\(G\\) action. Linear spaces are meaniningless without group actions.
In real life, vector spaces come this way, because of symmetry. So we shoudl think
of them like that.

The next natural thing to do when doing linear algebra is to study maps between
the objects. What is the correct notion of a map between vector spaces with \\(G\\)
actions? (obviously a natural transformation). That is, a linear transformation 
that's compatible.

Let \\(W,W^{\prime}\\) be two \\(G\\)-vector spaces. Define a \\(G\\)-equivariant 
linear transformation \\(W^{\prime}\to W\\) (or morphism of \\(G\\)-vector spaces)
such that it commutes with the action. So that for every \\(g\in G\\),
the obvious square commutes.

Schur's Lemma. ("There are lemmas that are really worth a thousand" something).
Consider a morphism between irreducible representations. Then it's either an isomorphism
or trivial. If \\(W=W^{\prime}\\), then the transformation is scaling.

Proof: We have that \\(T\rho_1(g) = \rho_2(g)T\\). We have that the kernel is \\(G\\) invariant
and the image is also \\(G\\) invariant. (Do element chase in diagram if not convinced).
The only way to resolve this is being either \\(T\\) is isomorphic or trivial.

For the second one, consider an eigenvalue \\(\lambda\\), so \\(Tw = \lambda w\\). We have that 
\\(T - \lambda I : W \to W\\) has \\(w\\) in the kernel and it's \\(G\\)-equivariant. 
Thus it has to be trivial. Hence \\(T = \lambda I\\).

# PLV Lunch

Discussion about Adam's paper/vision.

# Categorical Logic

Coherent Topoi. TODO.

# AI Mathematician UROP

Read DeepMath. They used Mizar. The problem they focus is *premise selection*. Basically,
you want to choose a set of axioms/premises so that you can solve in limited time a theorem,
with a given solver that will actually mix these steps. Previous efforts in ML didn't use DL.
They basically apply a RNN/CNN on character level on the Mizar corpus (whcih mainly important
because of size I guess) and tested on things not proved automatically. Managed to prove 7% of
these, or around 823. 

Note that Mizar is first order, so it could be embedded in Coq. Given that the problem here is 
combinatorial explosion, this could be good or bad. 

They kind of use Mizar as an (open ai style?) environment for the machines to play, except not 
interactive. 

TODO: Write more. 

The next paper is Deep Network Guided Proof Search.