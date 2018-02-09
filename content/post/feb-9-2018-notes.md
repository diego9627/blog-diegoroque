---
title: "Feb 9 2018 Notes"
date: 2018-02-09T01:44:41-05:00
draft: false
tags: ["18.702", "CatLog"]
---

# 18.702


Although a subrepresentation is just a subfunctor, the definition given is 
G-invariant subspaces. So technically it doesn't have to be a representation. 
But it is, because we have it's \\(G \to (V\to V)\\), and we can restrict the 
invariant subspace in the function and get \\(G \to (W\to W) \\).

Goal: Classifying "atomic" representations. A representation is irreducible 
if it's "prime" in a sense. If it doens't have proper and nontrivial subrepresentations.

If \\(G\\) is abelian, the all irreducible are 1-dimesional.

Note that all 1-dimensional representations are multiplying by root of unity.

If we have that \\(G = \langle g\rangle\\) is cyclic, then consider the representation 
\\(\rho : G \to GL(W)\\). We have that \\(\rho(g)\\) is a linear transformation of \\(W\\).
We can choose a basis that makes it a jordan linear form. Consider \\(\rho(g^n)=\rho(e)=I\\).
This is clearly, as  amatrix, the n-th powers of jordans. So the only possibility is that 
each block is identity, so 1x1. So \\(\rho(g)\\) is diagonalizable, and each basis element 
gives a g-invariant subspace. Thus these are the 1-invariant decomposition. 

Averaging trick: For a finite group, consider \\(\sum_{g\in G} \rho(g)\\). This will 
satisfy certain properties. In particular, if we apply any \\(\tilde{w}\\) to it, 
it will return a constant fixpoint of all representations. It might be zero though.

# CatLog

Define topos as a category equivalent to sheaves on a site, so \\(X\simeq \text{Sh}(C,J)\\).
We can prove A pretopos is a topos.
We can prove that this is equivalent to a left exact localization of preshaves on a category.
Assuming the second, we essentially go through the axioms one by one and use that 
set is a pretopos, that limits of functors are computed pointwise, and that \\(X\hookrightarrow \text{Sh}(C,J)\\) has a left exact adjoint (so the localization preserves lim).

We haven't proved that there exist a localization. I don't quite remember how I did it at DRP
probably something regarding presentable, but here we gave the explicit construction of 
applying the transformation twice.

Ok, from the DRP proof, The Vopenka principle says that every full subcategory \\(D\hookrightarrow C\\) that is closed under limits is a reflective subcategory.
We have that sheaves are closed under limits, so it has a left exact localization. We have 
that Set is locally presentable, and that \\(Set^C\\) is locally presentable, hence 
the category of presheaves is locally presentable. Hence left exact adjoint.

But this is kinda cheating, because it's an axiom.