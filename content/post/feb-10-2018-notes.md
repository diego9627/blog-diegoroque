---
title: "Feb 10 2018 Notes"
date: 2018-02-10T07:22:11-05:00
draft: false
tags: ["Chapter0","18.701"]
---

# Algebra : Chapter 0 

Most things are done using maps, almost nothing with set theory. Every kernel
is a normal subgroup and every normal subgroup is a kernel, so we technically
don't lose anything by being map-centric and thinking normal subgroups 
in a kernel-first fashion. In particular, the kernel of \\(G\to G/N\\).

## Kernel stuff

We have that the kernel of \\(\phi : G \to G^{\prime}\\) has the universal property 
that any map 

Usage of the concept: To check that \\(\frac{G_1\times G_2}{H_1\times H_2}
= \frac{G_1}{H_1}\times \frac{G_2}{H_2}\\) we do the following.

We have the projections \\(\pi_i : G_i \to G_i/H_i\\). 
We have projections \\(G_1\times G_2\to G_i\\) (bc product) and \\(G_i\to G_i/H_i\\).
Hence we have maps \\(G_1\times G_2 \to G_i/H_i\\). By the property of the product, we can 
consider the map \\(G_1\times G_2\to (G_1/H_1)\times (G_2/H_2)\\). We can check that the 
kernel of this is \\(H_1\times H_2\\) and conclude.

Kernel is initial among those who precompose to trivialmap, cokernel among those postcompose.
We have also that \\(\text{coker }\phi = G/\text{im }\phi\\).

## Group actions

Groups actions are just morphisms \\(G\to \text{Aut }_{Set}(A)\\) for some set.
Equivalently, they are functions \\(G\times A\to A\\) with nice enough properties.
Equivalently, they are objects of \\(\text{Set}^{G}\\). That is, they
are functors from \\(G\\) to Set. These are called G-sets, and the view as functors 
gives the morphisms between them. 

## Group _objects_

Groups are based in Set. This sucks. We define a group object in a category \\(C\\) to be the 
basically the same but changing everythign to C and rules to commutative diagrams.
More precisely,  \\((G \in C, m: G\times G\to G, e : 1\to G, \iota :G\to G)\\) that follows 
the common group laws but diagramized will be a group object. 

In set this is just an object. But in Top, this is a topological group (So there's more sharing 
than just the name and syntax!), in manifolds is lie group. Etc. Note that \\(\times,1,\to,\\)etc
have different meanings in different categories. For example, when considering Top,
we immediatly get that \\(m:G\times G\to G\\) must be a continuous function and the product
will have the product topology.

## Rings

We have that the endomorphisms of a group have addition, herited from homomorphims from G to G,
herited from G, and composition. Turns out this form a ring.

Ring \\((R, +, \cdot)\\) is a group in \\((R,+)\\), a monoid in \\((R,\cdot)\\), and 
distributive law.



# 18.702

For the pset. The challenge problem is roughly like this. For cyclic groups of 
order \\(n\\), the answer is clearly \\(n\\). For products, the answer is clearly
the product. From this we conclude that for abelian groups, their size is the  answer.

Now, note that if we have a representation \\(\rho: G \to \text{GL }(1,\mathbb{C}) = \mathbb{C}^{*}\\)
, then we are sending a group to an abelian group. By the universal proper of the abelianization
of a group, this has to factor through it. In particular, there is a one to one correspondence
between linear representations of order \\(1\\) and linear representations of their 
abelianization.

Hence in general the answer is \\(\lvert\frac{G}{[G,G]}\rvert\\).

It appears that in general the way to use these kind of factor throuugh properties is something 
like "ugly thing maps to nice thing, thus it can be seen as ugly thing to nice approximation 
(a map that we know), then nice approximation to nice other thing, a map that is nice".
Thus we can deal with the complexities of being ugly in a single map.