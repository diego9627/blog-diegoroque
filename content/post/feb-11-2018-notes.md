---
title: "Feb 11 2018 Notes"
date: 2018-02-11T08:19:47-05:00
draft: false
tags: ["ML", "18.702", "Chapter 0"]
---

# ML

Not much to say. Need to code more.

# 18.702 (Self Study)

## Pset

Solved the pset. On one problem, relying in the categorization of finite abelian groups 
can be avoided by considering the whole group and proving that since the image commutes
and  each one diagonalizable, then conclude everything is mutually diagonalizable. 

## Linear representations

We call \\(R: G\to \GL_n\\) a matrix representation. Given a representation 
\\(\rho: G\to \GL(V)\\), we say \\(\chi : G\to \C\\) such that 
\\(\chi(g) = \text{trace }\rho(g)\\) the character of \\(\rho\\).

We have that \\(\chi(1)\\) is the dimension of \\(\chi\\) (and also \\(\rho\\)).
We have \\(\chi(g)=\chi(h)\\) if \\(g,h\\) belong to the same conjugancy class.
Call functions of the form \\(G\to \mathbb{C}\\) which have same values for conjugate elements
class functions.

Let \\(\langle\chi_1,\chi_2\rangle = \frac{1}{|G|}\sum_g \overline{\chi_1(g)}\chi_2(g)\\).
We have that this is hermitian and the characters of irreducible functions
are an orthonormal basis over class functions. 

In particular, if we have a representation \\(\rho\\) with character \\(\chi\\), and irreducible
representations \\(\rho_1,\ldots,\rho_k\\) with haracters \\(\chi_1,\ldots,\chi_k\\), then let 
\\(n_i = \langle \chi, \chi_i\rangle\\).
We have that \\(\rho = n_1\rho_1\oplus\cdots \oplus n_k\rho_k\\).

## Permutations in linear

Suppose \\(G\\) acts on \\(S\\). Then we can view this action as a morphism 
\\(G\hookrightarrow S_G\\). By letting \\(S_n\\) act on the coordinates,
we get a representation \\(S_n\hookrightarrow GL_n\\).
Hence we can view acting on a set as a representation \\(\rho:G\hookrightarrow GL_G\\).
If \\(\chi\\) is its characteristic, note that \\(\chi(g)\\) is the size of the orbit of \\(g\\).

Now, since a group acts on itself, we can create a representation and a character out of this.
Call this \\(\rho^{reg},\chi^{reg}\\) the regular representation and character. This 
is just \\(\chi^{reg}(1)= 1,\chi^{reg}(g) \neq 1 \\) for \\(g\neq 1\\).

## Schur's lemma

If we have \\(\rho:G\to GL(V), \sigma :G\to GL(W)\\) are represenntations, then we call
a linear transformation \\(T:W\to V\\) a \\(G\\)-invariant if \\(T(gw) = g T(w)\\).
That is, if \\(T\circ \sigma(g) = \rho(g)\circ T\\). Recall that representations are 
just functors. This just means that a \\(G\\) invariant linear transformation is a natural 
transformation from \\(\sigma\\) to \\(\rho\\).

# Chapter 0

We have that if \\(G\\) is an abelian group then \\(End(G)\\) is a ring.
In particular, \\(End_{Ab}(\mathbb{Z})\simeq \mathbb{Z}\\).

We have that if \\(R\\) is a ring, right multiplication \\(r\mapsto (r\cdot) :R\to Aut(R )\\)
is a ring homomorphism.

You can start considering modules by using these things. 