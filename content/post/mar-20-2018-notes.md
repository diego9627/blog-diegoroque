---
title: "Mar 20 2018 Notes"
date: 2018-03-20T09:42:30-04:00
draft: false
tags: ["18.175", "18.408"]
---

# Levy inversion

Levy inversion formula 

$F_{\xi}(x_2)  - F_{\xi}(x_1) = \lim_{\delta \to 0} \frac{1}{2\pi} \int\phi(t)e^{-\frac{\delta^2t^2}{2}}\left(\frac{e^{-itx_2} - e^{-itx_1}}{-it}\right)$

Corollary: If $\int_{-\infty}^\infty \left|\phi_{\xi}(t)\right| dt < \infty$,
then $\xi$ ahs density $p$ given by $p(x) = \frac{1}{2\pi}\int_{\mathbb{R}}e^{-itx}\phi_{\xi}(t)dt$.

Higher dimensions:

$\xi_1,x_2,\ldots,\xi_k$, encode everything in their joint characteristic function
$\phi_{\xi_1,\ldots, \xi_k}\left(t_1,\ldots,t_k\right) = \mathbb{E}\exp\left(i\sum_{j=1}^k\xi_jt_j\right)$.

Application: Gaussian vectors,

Definition: $\xi_1,\ldots, \xi_k$ is a gaussian vector if either 

1. $\forall c_1,\ldots, c_k$ deterministic constants, $\sum_{i=1}^k c_j\xi_j$ is a gaussian random variable.
2. $\phi_{\vec{\xi}}(\vec{t}) = \exp\left(i(\vec{m},\vec{t}) - \frac{1}{2}(C\vec{t}, \vec{t})\right)$, where $\vec{m}$ is vector of means, $C$ is the covariant matrix, such that $C_{a,b}=\mathbb{E}(\xi_a - m_a)(\xi_b -m_b) = Cov(\xi_a,\xi_b)$. What's happening is $(C\vec{t},\vec{t}) = \sum_{a,b}t_aC_{a,b}t_b$.
3. $\exists \vec{\xi}'$ vector of i.i.d. normal gaussians such that $\vec{xi} = A\vec{\xi}'+\vec{m}$ where $A$ is a deterministic matrix and $\vec{m}$ is a deterministic vector.
4. If $C$ is nondegenerate, $P_{\vec{\xi}}(\vec{x}) = \frac{1}{\sqrt{(2\pi)^k \det C}} \exp\left(-\frac{1}{2}(\vec{x} - \vec{m})^T C^{-1}(\vec{x}-\vec{m})\right)$.

Theorem: All these definitions are equivalent.

From 2) to 1) Take characteristic function of multivariate and evaluate the sum of characteristics.

From 1) to 2), we will compute the characteristic function of $\sum_j c_j\xi_j$. This turns 
out to basically be the thing you want, after plugging in $t = 1$ and $\vec{c}=\vec{t}$.

From 2) to 3), the information to build $A$ is in $C$. Diagonalizing $C$, we have $C = B^T diag(\lambda_1,\ldots, \lambda_k) B = A^TA$, by symmetry of $C$. Then we have $\vec{\xi} = A\vec{\xi'} + \vec{m}$. Then it's just checking.

From 3) to 2), just compute it. (actually, if you do this, you get faster that you want $C = A^TA$)

From 3) to 4) and back, we just have to compute it. Same diagaonalization.

Corollary 1: Guasian vector is uniquely defined by its mean and covariance.

Corollary 2: For a gaussian vector (so jointly guassian), noncorrelated (cov = 0) implies independent

Corollary 3: For gaussian vector, pairwise independence iff joint independence.

Corollary 3 is not true in general. Classical example: $\xi_1,\xi_2$ bernouilli, $\xi_3 = \xi_1 \otimes \xi_2$. You can check pairwise independent, but they aren't jointly independent.

Theorem: $\phi_n$ characteristic functions of $\xi_n$, then if $\phi_n \to \phi$
converges pointwise and $\phi$ is continuous at zero, then $\phi$ is a characteristic function 
of some $\xi$ and $\xi_n \to \xi$ in distribution.

Proof: This follows a kind of compactness argument called tightness. A general scheme for probability proofs/papers is the following (about sequence): Given the sequence, you find a subsequence that converges. Then you prove that all subsequence converge to the same thing. This implies the general has a convergence.

Theorem (thightness): Let $\xi_n$ be random variables such that $\forall \varepsilon > 0 \exists C$ such that $\sup_n \mathbb{P}[|\xi_n| > c] <\varepsilon$. Then $\xi_n$ has a subsequence converging in distribution.

Proof: We have that $0\leq F_{\xi_n}(x)\leq 1$. Choose a subsequence $n_k$ such that 
$F_{\xi_n}(x) \to H(x)$ for all rational $x$.

Note $H$ is monotone. Define $F_\xi(x)$ to be the right limit of $H$ along rationals. 
It might even be different to $H$ in rationals.
Check properties of $\xi$. 

1. Monotonicity. By construction.
2. $F_\xi(-\infty) = 0, F_\xi(\infty) = 1$. This is directly tightness.
3. $F_\xi$ is right conditions. Follows from monotonicity and limits. First rationals then general.
4. Convergence at each point of continuity

Hence the theorem.


Construct the characteristic function.

Once you have this, it follows by levy inversion that $\xi_n\to\xi$ in distribution.

# 18.408
 
## Convex geometry

Where's high dimensional volume concentrated?

One of the more counterintuitive properties is where volume is concentrated. 
In $[-1,1]^2$, to get one percent of the volume we need the subcube $[-0.1,0.1]$.
For $[-1,1]^{100}$, we need $[-0.955,0.955]$. SO most of the volume is concentrated in the 
boundary.

How big a cube do you need to get total volume $1$? Obviously $[0,1]^n$.

How big a sphere do you need to get total volume $1$? The general formula 
is $\frac{r^n \pi^{\frac{n}{2}}}{\Gamma\left(\frac{n}{2} + 1\right)}$ 
which is approximately $\left(r\sqrt{\frac{2\pi e}{n}}\right)^n$. 
So the radiuous needed is about $\sqrt{\frac{n}{2\pi e}}$. So balls need a bigger radious.

That is, a ball is drastically smaller than the cube. Or is it?
The diameter of the unit cube is $\sqrt{n}$, so it's the same order.  There's a factor thrown
in, but morally it's basically proportional. 

This also menas that the corners are the typical points, if we throw a random thing, it would
get near the corner.
The reason you need to believe this is chernoff bounds. 

How ig is an $(n-1)$-dimensional slice of the $n$ sphere? How does the volume of the slice 
vary as a function of distance from the equator? "How much is the earth between the tropics".
This is weird, because things are closer to the equator, but away from the border.

So most of the volume lies near the origin.
But each hyperplane is the same, so most of the volume lies near to any subspace of 
dimension $n-1$.

One would reason that their intersection would be big also, but it's actually false.

The good way to think about it is to think as independent gaussians.

Suppose you have $x_i \sim N(0,\frac{1}{n})$. We have that $\mathbb{E}(\sum x_i^2) =1$.

## The Polar of a polytope 

Suppose we have a (bounded by definition) polytope $C \subset \mathbb{R}^n$ that contains 
the origin. You can write it as set of points satisfied some inequalities,
$C = \{X : a_i \cdot x \leq b_i \forall i\in [k]\}$. You can scale the 
inequalities such that WLOG $b_i = 1$. Note we are taking $a_i \in \mathbb{R}^n$.
We can form a new polytope called the $polar$ of $C$
given by $C^* = conv(a_1,\ldots,a_k)$.

It kinds of looks like inversion, hmm. It is apparently a projective transformation.

### Some properties of the polar 

Define $C^* = \{x | c\cdot x \leq \forall 1\}$. This is in the dual/constraint space.

If $A\subset B$, then $B^* \subset A^*$. We have that if $b\in B^*$ means that $b$ is a constraint 
that $B$ satisfies. So $A$ satisfies it. So $b\in A^*$. 
We will prove that $(C^*)^* = C$.

Theorem (Separating hyperplane theorem): If $K$ is convex and $p\not\in K$, there is a 
hyperplane that strongly separates them.

Proof: Take $q$ with $q\cdot K \leq 1$ and consider $q\cdot p$. 
There's a minimum, because of compactness. This minimum can't be less or equal to $1$,
because $p\not\in K$. Hence we have a strongly separating plane.

We have that $K\subset (K^*)^*$ by tautology, and the other direction by separating hyperplane.

### Norms

We will now treat only origin symmetric convex bodies.
There's a connection between norms and convex bodies.
If we have a norm $q$, we can build $B_q = \{x : q(x)\leq 1\}$. This is clearly convex.

If we have an origin symmetric $B$, define the Minkowski functional
$p_B(x) = \inf_{\lambda > 0}\{\lambda : x\in \lambda C\}$. That is, smallest inflation 
so that $x\in \lambda C$. Sometimes denoted as $\lVert x\rVert_C$.

We have $B_{p_C} = C$ and $p_{B_p} = p$.

For any norm $q$, we can define it's dual by $q^*(x) = \sup_{v\neq 0}\frac{x\cdot v}{q(v)}$.
This is the same construction almost by definition as polaritiy.

That is, $(q^*)_C = (C_q)^*$.  Things commute, etc, etc.

For $p\geq 1$, we have the $p$-norm $\lVert x \rVert_p = \sqrt[p]{\sum_i x_i^p}$. 
Then if $\frac{1}{p} + \frac{1}{q} = 1$,
the norms for $p$ and $q$ are dual. 

### Fritz John theorem

How far can $C$ be from $B_2^n$? How can we approximate $C$ with euclidian balls? What's
the right way to ask this? Bad idea: What's the least $t$ such that 
$aB_2^N \subset C \subset at B_2^N$.

Good idea: What's the smallest $t$ such taht for some elipse $L$, we have $L\subset C\subset tL$.

Banach-Mazur distnce $d(K,L)$ is the least positive $d$ such that a linear image $L'$ of $L$
is such that $L'\subset K \subset L'$.

Note that $d(K,K) = 1$, so it's not actually a metric. But the log of it is a metric.

Fritz John Theorem: For any $n$-dimensional origin symmetric convex body $K$, we have 
$d(K,B_2^n)\leq \sqrt{n}$. 

That is, there exist some elipse $E$, such that $E\subset C\subset \sqrt{n}E$.

This is tight for the cube. If we don't require symmetric, the bound will be $n$ and the 
tight example is the simplex.