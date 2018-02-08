---
title: "Feb 7 2018 Notes"
date: 2018-02-07T23:30:14-05:00
tags: ["mathematics", "computer science", "18.408", "18.S996", "18.702", "CatLog", "NotAdjS"]
draft: false
---

Technically also some from February 6. Also not so much notes but key ideas. Or not even that.


# 18.408

Spectral graph theory. For each graph \\(G\\) consider a matrix \\(M\\), generated somehow. 
Then consider the eigenvalues of this \\(M\\). Study this, and this is basically spectral graph theory.
In particular, we view vectors as functions from the vertices to the reals or whetever field we are considering.
The "natural" or rather obvious one is the adjacency matrix. A better one is the Laplacian,
roughly \\(L = D - A\\), where \\(D\\) is the diagonal matrix with values in diagonal degrees
of the corresponding matrix and \\(A\\) is just the old adjacency matrix.

Magical stuff happens when you consider the eigenvalues of \\(L\\). 

# 18.S996

Condorcet: Suppose you have a group of people deciding something. What is the best way to do it?

Take two, suppose you have \\(n\\) people deciding something. Each has an (independent!)
probability \\(p\\) of being correct. If you decide by majority votes,
As \\(n\\) grows, it tends to \\(1\\) the prob of correctness. Moreover, it grows strictly monotonically.
This by some theorem whose name I don't remember.

If \\(p\\) varies with \\(n\\), the flip between \\(0\\) and \\(1\\) happens around 
\\(\frac{1}{2} + \sqrt{\frac{1}{n}}\\)

If you consider different voting mechanisms of the form \\(f : \\{\pm 1\\}^{n} \to \\{\pm 1\\} \\), then 

* If \\(f\\) has no restrictions, best is majority, worst is -majority. Electoral
college also increases monotonically to \\(1\\) but slower than majority.
* If \\(f\\) is monotone, worst is constant.
* If \\(f\\) is fair (so \\(f(-x) = -f(x)\\), then worst dictator.

# 18.702

There's not much to groups. Not a lot of ways to study them. They are weird af. The multiplication table doesn't really tells us anything. 
On the other hand, we know a lot of two particular groups, \\(S_n\\) and \\(GL_n\\).

The permutation group is interesiting, because we have that every group is a subgroup of some permutation group (proof: check G action on G, or shout Yoneda Lemma and run away). This gives the idea of studying groups embedded in other groups.
We call \\(\rho\\) a permutation/linear representation if it's an homomorphism
from \\(G\\) to the permutation group/linear group. Basically a functor.

In algebra we are going to see a bunch of different objects and we are interested 
to study certain common things

* Equivalences
* Subobjects
* Morphisms
* Transformations between morphisms

For the most part, we are consider the linear case. What is a subrepresentation?
Well, it's a subfunctor. What is a subfunctor? A subobject in the category of 
functors. So here the natural transformations are objects. 
If a natural transformation is epi, it's epi pointwise. So a subfunctor of \\(F\\)
is \\(G\\) if \\(Gx\\) is a subobject of \\(Fx\\). In the case of linear subrepresentations,
this means that a subrepresentation is a representation to a subspace.

Much more categorical imho.

# CatLog

We have a coherent category ("weak pretopos"). We want a pretopos. We will first go through 
proper topos.

A category \\(C\\) with finite limits has a grothendieck topology \\(J : C^{op}\to Set^{C}\\) 
(can also be thought as just a collection) is a collection
of families of maps of the form \\( \\{ f_i : U_i \to X \\} \\), those are covering maps.
Note they can be thought as subfunctors of the representable functor on \\(X\\). This 
has to satisfy:

* Stability by pullbacks
* Composability of coverings (If you have coverings of objects and those cover a single one, then the nice thing happens)
* If an \\(f_i\\) has a section, the family is covering

A sheave satisfy that annoying to write sheaf condition.

The pair \\((C,J)\\) is a grothendieck site. The class of sheaves on this site is called a topos.

An interesting one, appart from the topological ones, is the following. Consider that 
\\(C\\) is categorical. We say \\( \\{ U_i\to X\\}\\) cover \\(X\\) if theres a finite union that 
covers it. 

# Not AdjS

Printed the paper?