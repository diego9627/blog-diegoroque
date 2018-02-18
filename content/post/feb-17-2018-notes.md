---
title: "Feb 17 2018 Notes"
date: 2018-02-17T10:37:32-05:00
draft: false
tags: ["AI Mathematician UROP", "MIT Categories Seminar"]
---

# AI Mathematician UROP

## Deep Math and Proof Search

Preliminaries:

* Mizar
* Prover E
    * Superposition Calculus
    * Knuth-Benedix
    * Together with Vampire, SPASS, CVC4, Z3 the core of *Sledgehammer*

The cost part is, well, costly so you have to prepare it a bit and interweave algebra and 
theorem proving so that there's no bottle neck.


DeepMath does clause selection, and deep guided proof search does clause order. So no "AlphaGo" stuff.

On more technical stuff, it uses WaveNet for the NN among others.

There's another paper that does AlphaGo stuff, [this one]
(https://aclweb.org/anthology/W/W16/W16-1309.pdf).

## PyTorch

Nicer than tf until now. Must check GPU servers. Remember to use `source activate root`.
Did some tutorials.

## Other papers

Made a arxiv-sanity account and added a bunch of papers.

# MIT Categories Seminar

## Metric realization of fuzzy simplicial sets. 

Consider the set \\(I = [0,1]\\) under the lower order topology. 
This means we can take sheaves on the relevant presheave category. 
This is actually not doing anything, because any presheaf is a sheaf here.
We have that \\(S : I^{op}\to Set\\) is a sheaf, then set \\(S^{\geq a}\\)
as \\(S((0,a)))\\). That is, elements of strength up to \\(a\\). If projections are injective,
call this a fuzzy set. Turns out this is basically a fuzzy set in the classical sense.

We have that the category of fuzzy sets to sheaves in \\(I\\) induces a forgetful functor,
and it's adjunction exists. We prove with this that fuzzy sets have arbitrary colimits.

We will have that a simplicial set is a contravariant functor from simplicial to fuzzy sets.
Alternatively, it's a contravariant functor from simplicial times \\(I\\) to sets with
certain properties.

Define uber metric spaces as metric spaces but it can be infinite and nonsymmetrical. 
Aka Lawvere metric spaces. Aka categories enriched with the monoidal poset 
\\(([0,\infty],\geq)\\). Anyway, this induces a category, where morphisms
are non-expansive.

This trivially has initial objects and arbitrary products. Coequalizers too with a bit more 
effort. Hence it has arbitrary colimits.

We can define a map \\(Re_0\\) from representable fuzzy sets to uber metric spaces.
After this, we can use colimits (so left kan extension) to define \\(Re\\) 
from fuzzy sets to uber metric spaces. This construction preserves colimits, so 
there's a right adjoint \\(Sing\\) from ultrametric spaces to fuzzy sets.

We have that \\(Sing(Y)\_n^{<a} = Hom\_{UM}(Re(\Delta\_{<a}^n), Y)\\).

Then some (persistent) cohomology stuff.

## UMAP

Supposedly this applies the previous paper and it's better than tSNE. 
Assumess little, biggest assumption being uniform distribution. This is overcomed by
also approximating a metric for which it's going to be uniform.

* Topological manifold : Locally euclidean
* Differentiable : locally vector space
* Riemannian manifold : Has inner product on tangent space

We have that a ball in the ambient space will have around the same number of points.
Thus we can renormalize in each point according to the k-th nearest. Essentially, we create 
a distance/metric per point. Now we the problem is that these metrics can be very inconscistent.
Hence we have to convert them into global structure. Here we use fuzzy simplicial sets.

What follows is basically Spivak's paper rewritten. Except that he focuses on finite 
versions of those categories.

Thus to handle incompatible metric spaces, we translate each metric into a fuzzy
simplicial set. By adjointness, this preserves the metric information. To homogenize/normalize/
ironing out incompatibilities of the fuzzy simplicial sets, we can take fuzzy unions.
We get a single fuzzy set, which should have the relevant information.

In particular, if we were to have another data set and apply the same procedure, we will end up
with another fuzzy simplicial set. This means we have two fuzzy simplicial sets,
so if we can compare them and get a comparison of the metrics. 
Hence if we were to find an appropiate (low-dimensional) alternative, we would find 
a reduction in dimentionality.

To compare two fuzzy sets, we define a cross entropy on classical fuzzy sets and translate
"categorical" fuzzy sets to classical. Finally we can use stochastic gradient descent
to find the ideal dimensionality reduction.

Then stuff to implement this nicely.

The results are that UMAP is comparable with tSNE when reducing to two/three dimentions.
UMAP is way faster, single threaded python is faster than single threaded optimized C++ tSNE.
It has better asymptotic performance in general.