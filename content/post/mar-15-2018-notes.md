---
title: "Mar 15 2018 Notes"
date: 2018-03-15T09:38:01-04:00
draft: false
tags: ["18.175","18.408","18.702","Chapter 0"]
---

# 18.175

## 0-1 Kolmogorov

We have the law of large numbers, that if $\xi_i$ are independent, then 
$\frac{1}{n}\sum_{i=1}^n \xi_i \to \xi$ almost surely to the average.

Kolmogorov $0-1$ law. Have $\xi_i$ independent and $\mathcal{A}_n$ the $\sigma$-algebras
spanned by $\xi_1,\ldots,\xi_n$ . Consider $A_{\infty} = \bigcap_n A_n = \mathcal{T}$, 
the tail sigma algebra.
Events that are things that "everything" is needed, but not anything in particular.

Kolmogorovs $0-1$ law states that for all $A \in \mathcal{T}$ or $P(A)$ is $0$ or $1$.
The idea of the proof is that if $A\in \mathcal{T}$, then $A$ is indpendent from itself.

We have that $A$ is independent from all $\xi_i$. Hence it's independent
for all the $A_n$. Hence it's independent from $\mathcal{T}$. Thus $A$ and $A$ are independent.
Normally to rule out one case, then you bound it.

Example: Let $\xi_i$ independent, let $f(t) = \sum_{i=1}^\infty \xi_i t^i$. Claim:
Radius of convergence is almost surely a constant.
Note that we can write $\frac{1}{R} = \limsup_n{\xi_n^{\frac{1}{n}}}$. We have that 
$P[\frac{1}{R} \in (a,b)]$ is zero or one for every interval. But it can't be one for two
disjoint intervals. The only way for this to be possible is for $R$ to be a constant (a.s.)

## Characteristic

Let the characteristic function fo $\xi$ be $\phi_{\xi} = \mathbb{E}(\exp(it\xi))$. 
Note that since it's real, $\exp(it\xi)$ is bounded, so it exists.

We have that $|\phi_\xi(t)| \leq 1$ (obviously), $\phi_\xi(0)=  1$ (obviously),
 and $\phi_\xi$
is uniformly continuous over $t\in \mathbb{R}$.

To see this last one, compute the difference, factour out the first one, factor the absolutes
and remove the one, and we get 

$$|\phi_\xi(x) - \phi_\xi(y)| \leq \mathbb{E}|1 - e^{i\xi(y-x)}|
= \mathbb{E}|1 - e^{i\xi(y-x)}|I(|\xi|\leq c) + 
 \mathbb{E}|1 - e^{i\xi(y-x)}|I(|\xi|> c)
$$

the first term goes to $0$ as $|x-y|\to 0$. The second term is bounded by $2P(|\xi|>c)$. So
the limit is bounded by every $2P(|\xi|> 0)$, which goes eto $0$ as $c\to 0$.
So it tends to $0$.

Another property, we have that $\forall t_1,\ldots, t_k$, consider $A = (\phi(t_i-t_j))_{i,j}$
, then it is positive semidefinite. Alternatively, 
$\sum_{i,j=1}^k x_i\overline{x_j} \phi(t_i -t_j) \geq 0$.

Theorem (Bochner):
Any function that satisfies these four properties, is a characteristic function.
Won't be proven or used.

Other properties:
$\phi_\xi(-t) = \overline{\phi_\xi(t)}$. $\phi_{A\xi + B} = e^{iBt}= \phi_\xi(At)$.
$x_i$ independent, then $\phi_{\sum_i \xi_i} = \prod_i \phi_{\xi_i}$.

If $\xi \sim N(\mu, \sigma^2)$, then $\phi_\xi(t) = \exp(i\mu t - \frac{\sigma^2t^2}{2})$.
To prove this, we only consider $\xi \sim N(0,1)$. Computing, we have

$$\phi_{\xi}(t) = \frac{1}{\sqrt{2\pi}}\int_{\mathbb{R}} e^{itx - \frac{x^2}{2}}dx
= \frac{1}{\sqrt{2\pi}}e^{-\frac{t^2}{2}}\int_{\mathbb{R}} e^{-\frac{(x-it)^2}{2}} dx
= \frac{1}{\sqrt{2\pi}}e^{-\frac{t^2}{2}}\sqrt{2\pi} = \exp(-\frac{t^2}{2})
$$

Now, assume $\mathbb{E}\xi^k$ exist (note this implies all lower moments exist).  
Then $\phi_\xi(t)$ is $k$ times differentiable.
Note that moments not necesarily exist, like the mean for the Cauchy.
We have that $\frac{\delta}{\delta t}\phi_\xi(t) = i^k\mathbb{E}\xi^k\exp(it\xi)$

Now to prove this property, obviously we will have to do some swap of integrals
and derivatives. Let's see how that works. Shoot, we will do the derivative by hand.
We will procede by induction

$$\left|\frac{\phi^{(k)}(t + \Delta) - \phi^{(k)}(t)}{\Delta}
- i^{k+1}\mathbb{E}\xi^{k+1}e^{it\xi}
\right| =
\left|
\mathbb{E}e^{it\xi}\xi^k\left(\frac{e^{i\Delta\xi} - 1}{\Delta}-i\xi\right)
\right|
$$

Now, note that $\left|\frac{e^{i\Delta\xi} - 1}{\Delta}\right| = 2 \left|\frac{\sin(\frac{\Delta\xi}{2})}{\Delta} \right|\leq \left|\xi\right|$
since $|\sin(x)| \leq |x|$. 

Then we apply the dominated convergence theorem, and see that the expectation tends to $0$,
since the function tends pointwise to $0$.

By a corollary, we can write $\phi_\xi$ as the partial expansion plus lower terms.

Levy Inversion formula: Cummulative distribution from characteristic.
Let $\xi_1,\xi_2$ points of continuity of $F_\xi(x)$, then 

$$F_\xi(x_2) - F_\xi(x_1) = \lim_{\sigma \to 0}
\frac{1}{2\pi} \int_{\mathbb{R}}\phi(t)e^{-\frac{\delta^2t^2}{2}}
\left(\frac{e^{-itx_2} - e^{-tx_1}}{-it}\right)
$$
where we can think $\sigma$ as a smoothing factor.

Proof: Cosider $\xi + Y_\sigma$ where $Y_\sigma \sim N(0,\sigma^2)$ independently. Note it's
characteristic function is $\phi(t)e^{-\delta^2t^2}{2}$. Basically we are doing smoothing
with gaussian noise.
Compute the density of sum, we have 

$$P_\sigma(x) = \int_{\mathbb{R}} \frac{1}{\sigma \sqrt{2\pi}}
e^{-\frac{(x-y)^2}{2\sigma^2}}dF_\xi(y)
$$

equations, then finish with $\xi+Y_\sigma \to \xi$ in distribution as $\xi\to 0$.


# 18.408 (Notes to be sent, Lecture 10, 11?)

Effecive Resistance Examples: 
Picture Two big K_n, connected with a path.

Four blobs, connected in a square. 

Three blobs, in triangle. ONe side one edge, other side  two edges, other four.
One edge more expensive than two more than four, more than inner.
Think of it as energy required to rout.

Diamond, plus one from top to bottom. Reming top to bottom doesn't matter,
because there's parallelism. On the other hand, remove one inside you will have a bottleneck
on one edge everybody has to traverse, regardless of fastness of the initail paralelism.

Today menu: More on graphs, electrical flows. Start convex geometry.

## Laplacians and electrical flow

Orient edges aribtrarily. $U$ = edge-vertex adj matrix. $C = diag(c)$. 
$r_e = \frac{1}{c_e}$. $U(e,v) = 1$ if $v$ head of $e$, $-1$ if tail, $0$ otherwise.
$L = U^TCU$

Ohm's law: $i = CUv$, $i\in \mathbb{R}^E, v\in \mathbb{R}^V$.
Conservation: $i_{ext} = U^T i$, $i_{ext}\in \mathbb{R}^V$

we get $i_{ext} = Lv$, $v = L^{+}i_{ext}$.
This is essentially all of highschool electrical currents.

$R_{eff}(e)$ = potential difference between endpoints when flow one unit from one endpoint to 
other = $u_eL^{+}u_{e}^T$

(Here $L^{+}$ is pseudoeinverse. Basically inverse outside kernel, zero in kernel of $L$)

## Energy Flows and Energy

Let $\chi_{i,j}$ = col vector with $i^{th}$ entry $1$, $j^{th}$ entry $-1$. That is, $e_i - e_j$,
possibly with a transpose.

Last time showed:

* Potentials given by $L^{+}\chi_{s,t}$
* Flow (currents) coming from potentails $v$ is $f = CUv$
  * that is, $f_{(i,j)} = \frac{v_i-v_j}{r_{(i,j)}}$
  * So currents given $CUL^{+}\chi_{s,t}$.
  * Effective resistance given by $\chi_{s,t}^TL^{+}\chi_{s,t}$
* Another way: Energy 
  * Energy of flow $f = \sum_{e\in E}f(e)^2 r_e = f^T C^{-1} f = (v^T U^TC) C^{-1}(CUv) = v^TU^TCUv = v^TLv$ 
  * Flow coming from potentials $v$ is $f = CUv$
  * Energy of flow is $f^{T}C^{-1}f = v^TLv$
  * For eletrical potentials, get $(L^{+}\chi_{s,t})^T L (L^{+}\chi_{s,t}) = \chi_{s,t}^TL^{+}\chi_{s,t}$

Electrical flow is the one that minimizes energy over all flows given the demands.

Can check:

* Electrical flow minimizes energy among all $s-t$ flows of value $1$.
  * Potential difference between $s$ and $t$ is the effective resistance
* Say potential difference betwen $s$ and $t$ to be $1$. Eleectrical flows potentials
minimize energy
* Implies rayleigh monotonicity theorem: adding edges decreases effective resistance

Question:

Have a graph $G$, vertices $x,s,t$ distinct. tart at $t$, stop when hits $s,t$. 
Let $F(x)$ is the probability that hits $s$ before $t$. How can we compute $F$?

Clearly $F(s) = 1$, $F(t) = 0$. If at $x$, we go to each neighbor with equiprobility.
This implies the next 

$$F(x) = \sum_{(x,y)}P(x\to y)F(s) = \sum_{(x,y)\in E} \frac{F(y)}{d}$$

hence $dF(x) - \sum_{(x,y)\in E}F(y) = 0$. Treating this as a vector, this says
$LF = u_{s,t}$. So a laplacian system. Thus, the answer is given by enelctrical potentials!
This generalizes, also can be thought as discrete harmonic functions. These are functions
that a boundary obey equal zero.

What does effective resistance correspond to?

## Some useful linear algebra facts

Let $A$ be $n\times m$ and $B$ be $m\times n$.

* "Most useful identity in mathematics" according to a friend of terry tao $\det(I_m + BA) = \det(I_n + AB)$
  * Proof: By a density argument, we can assume diagonability. We have that $BA$ and $AB$ have nonzero eigenvalues. Hence $I_m + AB$, $I_n+BA$ have same non-
  one eigenvalues. Thus we win, by multiplying.
  * Rescalling is useful:  $\det(zI_m +BA) = z^{m-n}\det(zI_n + AB)$
* Matrix determinant lemma: $\det(A + vv^T) = (1 + v^TA^{-1}v)\det(A)$
  * For the identity it's trivial. Otherwise, apply the identity case to $A^{-\frac{1}{2}}v$
  * The right way to do in general things of this form is to solve the identity, and then reduce to the case of the identity by reescaling.
* Cauchy Binet: $A,B$ as above when $m\geq n$. $\det(AB) =\sum_{|S|=n, S\subset[m]} \det(A_S)\det(B_S)$. That is, take all square sized submatrieces, multiply them, add them.
  * Proof: Note that the reescaling identity can be viewed polynomials on $z$. Vieweing the coefficient of $z^{m-n}$, we get $\det(z)
  * If you seen wedge products, this is the way to do it. It's just the definition of multilinear algebra.
* Special case: $\det(AA^T) = \sum_{|S|= n, S\subset[m]} \det(A_S)^2$

## Laplacians and Spanning Trees

How many spanning trees does a graph $G$ have?

Theorem: Kirchoff's Matrix-Tree Theorem: Number of spaning trees 

$$T(G) =\frac{1}{n}\lambda_2\ldots\lambda_n$$,

where $\lambda_i$ are the eigenvalues of $L_G$. 

(This will essentially just be a determinant)

Let $(LG)_{i,j}$ = matrix when taking out $i$-th row and $j$ column from $L_G$.
We can state the theorem as $T(G) = \det((L_G)_{i,i})$ for all $i$.

It's not the determinant of laplacian,b ecasue that is zero.
Note that $\det((L_G)_{i,i}) = \det((L_G)_{j,j})$ for all $i,j$.
Is it obvious for the tree? (not really)

Two proofs:

Selfcontained proof: Induction. For weighted graphs, count each tree as product of edges.
Think of trees with a particular edge $e$ and without that $e$. Check both sides of the equation.
If you delete the edge, then you get the solution of the graph minus that edge, so you can 
use the laplacian of that graph. If not, you paste both and recurse. Add. Finish.

Another proof: Apply special case of Cauchy-Binet to submatrices of size $n-1$. 
Note that $L = UU^T$, where $U$ is that previosuly defined $U$.
Take one vertex, a matrix of $n-1$ is $\pm1$ if it's a spanning tree and zero if not.
Then applying cauchy bennet, we win.

## Trees  and effective resistence

Question: What is the probability that a given edge $e = (s,t)$belongs to a spanning tree?
Answer: Effective resistance
Proof: Use the matrix determinant lemma. For $i\not\in (s,t)$,
$(L_{G/e})_ii + \chi_{s,t}\chi_{s,t}^T = (L_G)_{i,i}$. This since $\chi_{s,t}\chi_{s,t}^T$
is the laplacian of the edge $e$.

Finally, $P(e\in T) = 1 - \frac{T(G/e)}{T(G)} = 1 - \frac{\det((L_{G/e})_{i,i})}{\det((L_G)_{i,i})} = 1 - \frac{1}{1 + \chi_{s,t}^T(L_{G/e})\chi_{s,t}} = R_eff(e)$

## Convex Geometry dfinitions

A convex set is a set that's convex. Typical definition. Function is convex if stuff above 
it is onvex. Else if concave. A convex body is a compact (so closed and bounded) full-dimensional
(nonempty interior) set.

## Everything I needed to know about convex geometry i learned in ... um..

Keith Ball's survey he writes "All convex bodies behave a bit like euclidean balls."
Intuition works until it fails. Add a few shapes and the intuition is mostly right.
Euclidean ball, elipsoids, cross polytope, symplex, spheriacl cone, etc,
In almost everything we will prove, the extremal case is one of these.

Morally in convex geometry where volume ends up is counter intuitive, but it makes things clean.

# 18.702

The field of fractions satisfies the universal property that every arrow from a ring to a field
factors to the field of fractions of that ring.

A ring $R$ is noetherian if every ideal of $R$ is finitely generated.

Theorem: If $R$ is noetherian, submodules of finitely generated are finitely generated.

Structure theorem: Abeliang groups are sums of cyclic groups and free abelian groups. 

# Chapter 0

## Modules

Recall that an $R$-module is a ring morphism $R\to End_{Ab}(M)$. Clasically we think of $M$
as the module, and the laws are deduced (from? to?) the morphism.

We have that an $R$-algebra (with $R$ commutative) is a ring homomorphism $\alpha : R\to S$ such that $\alpha(R)$ is in the center of $S$. Note any $R$-algebra is an $R$-module.

We can essentially think of $\alpha(r)$ as being the embedding of $r$ into $S$,
and $\alpha(r)s$ as $rs$, where $s$ is a vector space. Hence this is the same information as
$S$ vector space with a binary operation $\cdot : S \times S \to S$, such that 
the regular things hold. 

That is, the category of $R$ algebras is the category of rings under $R$.

Note that since every ring $R$ has a canonical isomorphism from $\mathbb{Z}$ to $R$, we have that
they are a $\mathbb{Z}$-algebra. Hence $\mathbb{Z}$-Alg is just $Ring$.

Note that the trivial group has au unique module structure for any ring $R$, and it's a zero
object in $R$-mod (final and initial). A bijective isomorphism of $R$-modules is an 
isomorphism. Note that if $N,M$ are $R$-modules, the hom between them can also be seen 
as an $R$-module.

Submodules are kernels. Hence the right notion of quotient. Knowing the domain through the 
codomain. "Every monomorphism is a kernel" is a feature of abelian categories.

## Products, coproducts in $R$-mod

Finite products and coproducts in $R$-mod are the direct sum. Take morphism $\phi$.
 Kernels initial in factoring $\alpha \circ \phi = 0$. Cokernels initial in factoring 
 $\phi \circ \alpha = 0$. 

Kernel trivial iff morphism injective iff morphism mono. 
Cokernel trivial iff morphism surjective iff morphism epi. We have that cokernels
are also the quotient of codomain over image. 

Free modules and algebras are defined as the adjoint of the forgetful functor to set.
Equivalently, in the "most efficient way" so that it has at least a set of elements.

