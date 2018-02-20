---
title: "Feb 19 2018 Notes"
date: 2018-02-19T11:26:08-05:00
draft: false
tags: ["optimization urop", "plv meeting", "18.702"]
---

# Optimizatino UROP

Implemented proof automatization. Some changes in types. Fixed translation to Haskell 
then to Julia. 

# PLV Meeting

Showed the results to my advisor. Discussed about doing a double major, mainly for MEng.
Turns out I can substitute classes for harder ones and people have done that.
I'll probably do this.

# 18.702 (Self Study)

## Orthogonality theorem

If we have two linear transformations \\(A\\) and \\(B\\), we can consider the linear 
transformation \\(A\otimes B\\), which can be thought the space of linear transformations from 
\\(A\\) to \\(B\\). In terms of matrices, it would be \\((M\mapsto AMB)\\).
If we have that the eigenvalues were \\(\\{\alpha_i\\},\\{\beta_j\\}\\),
the eigenvalues of the tensor product will be \\(\\{\alpha_i\beta_j\\}\\). 
In particular, the trace will be the product of the traces.
 
If we consider \\(\rho, \sigma\\) with representations on \\(A,B\\),
then considering the averaging map \\(\Phi(T) = \frac{1}{|G|}\sum_g \rho(g)^{-1}T\sigma(g)\\)
will send everything to a \\(G\\)-invariant map and will have invariant maps as fix points. 
Hence its image will be the invariant linear maps. We have that \\(\Phi : A\otimes B 
\to A\otimes B\\). 

We have that 

$$ \text{tr }\Phi = \frac{1}{|G|}\sum_g \text{tr }(T\mapsto \rho(g)^{-1}T\sigma(g))
= \frac{1}{|G|}\sum_g (\text{tr }\rho(g)^{-1})(\text{tr }\sigma(g)) 
= \langle\chi\_\rho,\chi\_\sigma\rangle
$$

Suppose \\(T\\) is equivariant and in the kernel of \\(\Phi\\). Then 
\\(T = \Phi(T) = 0\\). Hence the intersection of the kernel and the image of \\(\Phi\\) 
is trivial. Thus \\(A\otimes B = \text{im } \Phi\otimes \ker \Phi\\).
In particular, this means that \\(\Phi\\) on it's image its the identity, so 
the eigenvalues from this space sum up to the dimension. On it's kernel is null,
so the eigenvalues are all zero. Hence \\(\text{tr }\Phi = \dim \text{im }\Phi\\).

From this, we have that \\(\langle \chi\_\rho,\chi\_\sigma\rangle = \dim (\text{im }\Phi)\\).
Note that if \\(\rho,\sigma\\) are irreducible matrices, then either they are different and 
there are no invariant transformations except the trivial one (so \\(\dim (\text{im}\Phi)=0\\)),
or they are the same and the only ones are scalars of the identity (so \\(\dim(\text{im }\Phi)=1\\)). Hence \\(\langle\chi\_\rho, \chi\_\sigma\rangle = \delta\_{\rho,\sigma}\\).

Thus irreducible characters are orthonormal.

Now, consider the space of class functions \\(\mathcal{C}\\) and the space spanned by the 
irreducible characters \\(\mathcal{H}\\). Suppose you have \\(\phi\\) orthogonal 
to all irreducible characters.  Consider \\(T = \frac{1}{|G|}\sum_g \overline{\phi(g)}\rho(g)\\)
for some irreducible \\(\rho\\).
It's easy to see that it's \\(G\\) invariant from \\(\rho\\) to \\(\rho\\). 
Consider it's character. We have that the trace of \\(T\\) is 
\\(\frac{1}{|G|}\sum_g \overline{\phi(g)}\chi(g) = \langle \phi,\chi\rangle \\), 
which is zero since it is the linear combination 
of the dot product of \\(\phi\\) with irreducible characters. We have that by schur
\\(T\\) is the identity times a constant, and since the trace is zero, we have \\(T=0\\).
By semisimplicity, this also holds for every representation \\(\rho\\).

Applying this to the regular representation, we get that 
\\(\sum_g \overline{\phi(g)}\rho^{reg}(g) = 0\\). Note that the linear transformations
\\(\rho^{reg}(g)\\) are independent, since we have that \\(\rho^{reg}(g)(e_1) = e_g\\).
Hence the only way they can add to zero is that \\(\phi(g) = 0\forall g\in G\\).

Hence the only representation orthogonal to \\(\mathcal{H}\\) is the trivial one. 
Hence \\(\mathcal{H} = \mathcal{C}\\).

## Modules

A module is basically just a generalization of vector spaces. We have that if \\(R\\)
is a ring, then an \\(R\\)-module \\((V,+)\\) is an abelian group with an operation ("scalar 
multiplication") \\(\cdot : R\times V\to V\\) such that the natural things hold.

That is \\(1v = v, (rs)v = r(sv), (r+s)v = rv+sv, r(v+w) = rv + rw\\).

Note that a \\(\mathbb{Z}\\)-module is just an abelian group. When \\(R\\) is a field,
we have the free modules \\(R^n\\) of vectors of \\(R\\) defined in the obvious manner.
A submodule is defined in the obvious manner. Morphisms are defined in the obvious manner.

If \\(W\\) is a submodule of the \\(R\\) module \\(V\\), then \\(\overline{W}\\)
the set of additive cossets of \\(W\\) over \\(V\\) is also a submodule.
There's also a projection \\(\pi : V\to \overline{W}\\).

If we have the kernel \\(K\\) of \\(f: V\to V^{\prime}\\) contains \\(W\\),
then we can decompose \\(f\\) as \\(V\to \overline{W}\to K\\) in a canonical manner.
That is, there exist an unique \\(\overline{f}\\) such that \\(f = \overline{f}\circ \pi\\).

We have that if \\(K = W\\), then \\(\overline{f}\\) is an isomorphism. 

We have that  there's a bijection between submodules of \\(V^{\prime}\\) and 
submodules of \\(V\\) that contain \\(W\\), by the way of the inverse image and the image.
If \\(S,S^{\prime}\\) correspond to each other, then \\(V/S \cong V^{\prime}/S^{\prime}\\).

## Free Modules

We can consider matrices. We can redefine a bunch of the terminology in a consistent manner.
If \\(R\\) is not the zero ring, then the determinant is an unit iff it's invertible,
and invertible matrices are square matrices. Note that in \\(\mathbb{R}\\),
everything but zero is a unit, but in \\(\mathbb{Z}\\) only \\(\pm 1\\).

Any set of vectors \\(\mathbf{B}\\) of a module \\(V\\) induces a morphism \\(R^n\to V\\).
It generates if surjective, it is independent if injective, and it is a basis if the morphism
is an iso. Thus only (equivalents to) free modules have basis.

A free \\(\mathbf{Z}\\)-module is a free abelian group because obvious. To be honest, much
of the discussion of matrices is repeated as long as the rings are nice enough.

Note that if we want to prove something about matrices, like \\(\det A \det B = \det (AB)\\)
over modules, it suffices to do it on complex numbers. Suppose we are working on the \\(R\\).
There's a canonical projection \\(\phi: \mathbb{Z}[\\{x\_{i,j}\\}, \\{y\_{k,l}\\}]\to R\\).
We have that if we define \\(f\_S = \det (AB) - \det A \det B\\) for any ring \\(S\\),
then \\(\phi\\) links \\(f\_R\\) and \\(f\\) (over \\(\mathbb{Z}[\\{x\_{i,j}\\}, \\{y\_{k,l}\\}]\\)). We have that \\(f\_{\mathbb{C}}\\) is zero and we have that a polynomial in the complex 
is zero if and only if it's formally zero. Hence we have that the identity is true in the 
free abelian case. Hence projecting it is true for every case.
