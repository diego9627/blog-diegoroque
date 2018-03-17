---
title: "Mar 16 2018 Notes"
date: 2018-03-16T11:05:53-04:00
draft: false
tags: ["18.702"]
---

# 18.702

Localization with a prime ideal about dividing by not in the prime ideal. For example,
$\mathbb{C}[x]_{(x)}$ will be the rational fractions where the denominator is not a 
multiple of $x$. That is, the rational fractions evaluable at $0$.

Regarding the problem set, we have that injectivity is easy, because we can lift to rationals,
use the things for fields, then go back (carefully) to integers. 

Noethereian module: A $R$-module $M$ is noetherian if every submodule of $M$ is finitely 
generated. This is equivalent to $M_0\subset M_1\subset \ldots$ of submodules stabilizes.

Call a ring noetherian if it's noetherian as a module over itself.

Examples: The usual subjects, $\mathbb{Z}, \mathbb{C}[x]$, every principal ideal domain,
$\mathbb{C}[[x]]$. But we don't have that many more examples.

Hilbert basis theorem: If $R$ is Noetherian ring, then $R[x]$ is also noetherian. 
Note this implies that $R$ being noetherian lifts into $R[x_1,x_2,\ldots, x_n]$ is noetherian.

Intuitively this should be close to the nullsellenzats.

Lemma: A module $M$ over $R$ is finitely generated if $M$ is a quotient of a free module
of finite rank. That is, $R^N\to M$ is surjective. That is, there's no interesting behavior.
The proof is the obvious.

Lemma (Leading Coefficient lemma): 
Let $I \subset R[x]$ be an ideal. The leading terms of polynomials in $I$, together with $0$,
forms an ideal in $R$.

