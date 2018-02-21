---
title: "Feb 20 2018 Notes"
date: 2018-02-20T08:24:39-05:00
draft: false
tags: ["18.S996", "18.702", "ml", "Chapter 0"]
---

# 18.S996

## Martingale

Claim \\(M(t) = \sum_v d(v)V(v,t)\\) is a martin gale.

Proof: Check \\(E[M(t+1)|V(\cdot,t)]\\). This is 


Wald first euqation: If \\(T\\) is a stopping time with bounded expectation, then
 \\(E[M(T)]=E[M(0)]\\).

Second equation; If \\(E[(M(t) - M(t-1))^2 | T\geq t]\geq a\\), then \\(E[(M(t) - M(0))^2]\geq aE[T]\\).

Going to the voting model, choose the stopping time of everybody agreeing. Then we have that 
\\(E[M(0)] = \sum_i d(i)s(i)\\), and \\(E[M(T)] = p_1 dn \cdot 1+ dn p_0 \cdot 0\\)
and they are equal.
We also can prove that before stopping time, the variance is bounded below by \\(\frac{1}{d}\\),
hence the stopping time is bounded by the variance times \\(d\\), where \\(d\\) is the maximum.


\\(G\\) is a \\(\delta\\) expander graph if for all \\(A\subset V\\) st \\(|A| \leq n/2\\),
the boundary is at least \\(\delta |A|\\).

## Bribery in the Voter model

At *one* point we can brive \\(k\\) nodes from minus to plus. Which nodes to bribe?

Answer: Largest degree, because it increases the martingale.

There's no learning. Can't converge to majority without additional memory. There's
no local dynamics that converge to majority without additional memory.

## Strong Weak Voter Model

Edges are chosen poisson.

Keep also a strong/weak bit of information, appart from valence of opinion. Original all strong.
Strong always influence weak. If they are equally strong, you implement voting model.
Two strongs opposite cancel to weak, otherwise they stay the same. 
(maybe doesn't matter with voter model) With random probabilty, swap location.

Note weak people stay weak.

TODO: Code this maybe??

Claim: Connected (odd) graph converges to majority (ignoring strength).
Proof sketch: Opposite strong cancel out, so majority of strongs is kept. Eventually 
all strong are of one type. After that, it only takes time to their opinion to spread.
It's basically the voting model of cheaters.


Kinda weird that it works, becuase its not "nice"?

Reaserch Q: Find convergence time

## Computational models on graphs

More generally: which functions can be computed on graph? 
How much memory is needed? Eg: Can check two thirds of node 1?
Check cycle length 4? Relations to dna. Check [this](https://arxiv.org/pdf/1306.4151.pdf).

## Majority of neighbors

Usual stuff. Harder to analyze. Not all the nodes converge to same value. Very few tools.
Since update is \\(s(i,t+1) = sgn(Ws)\\), its matrix multiplication then nonlinearity.
Neural network vibes.

Nonconvergence: bipartite, alternating cycle, directed cycle.

It doesn't necessarily cnoverge, but it converges two length two. Hint/Proof Sketch:
Use potential function : \\(\sum\_{i\sim j} I[X(i,t) \neq X(j,t-1)] 
= \sum\_{i\sim j}(X(i,t)-x(j,t-1))^2 = U(t)\\).

Exercise: 1)\\(U(t)\\) is nonincreasing. 2) If \\(U(t)=U(t+1)\\), then \\(X(i,t+1)= X(i,t-1)\\)
for all \\(i\\).

Take \\(f\\) to be the majority of current opinions in majority dynamics.
It is monotone and fair. If the graph is transitive, then \\(f\\) is transitive. 
Then we can apply the theorem we first saw, and get that we don't lose the information.

If not transitive, there exist graphs where you can forget.

In the star, the center person half the time will be correct(ish),
half the time it will be random.

On expanders: For an expander if \\(p -\frac{1}{2}>>\sqrt{d}\\), then 
all converge to \\(1\\) with high probability.

Expander mixing lemma: 

$$ |E(A,B) - \frac{d|A||B|}{n} | \leq \lambda \sqrt{|A||B|} $$

# 18.702 (Class)

Proving orthonormality of characters. Also doing problems.

# Cartesian Bicategories

A bicategory consists of objects, called \\(0\\)-cells, morphisms \\(B(x,y)\\)
(1-cells), morphisms between morphisms \\(B(f,g)\\) (2-cells).
There's composition of morphisms, vertical of 2-cells,left and right whiskering 
(which I guess imply horizontal composition of 2-cells).
We don't have that \\(f = f\circ id_a\\), but we have that \\(f\simeq f\circ id_a\\),
a left unitor. Similiary with right. Similary we have a thing for associative 2-cells
(vertical) we have associator. Plus a bunch of laws.

So whereas in a strict 2-category, we would have literal equality on \\(f \circ (g \circ h)
= (f\circ g)\circ h\\), here we just have an equivalence. 

There's a coherence theorem turning each bicategory in 2-categories, and that's the greatest 
\\(n\\) for which this holds. It is locally posetal if \\(B(x,y)\\) is a poset.

# Interpretable Machine Learning Through Teaching

Train student normally, then train teacher by evaluating on examples the student needs to learn 
(learning itself being evaluated on the first step). This should select for the most "essential"
examples. 

In particular, the student is only trained once (so it's more like running an NN to interpolate 
the truth), so they are *not* trained jointly. Thus there's no collussion,
since they are actually different instead of essentially one lobotomized
brain. This is different from a network which in idea is two but in practice is one teacher
and student, which end up being optimized jointly and serving as one big thing.

(Also turns out more than one step of this is useless, optimizing jointly after is useless
in comparison)

That's roughly it. Train them separately, and they won't be able to collude, so it will
have to be more essential.  

Also interesting (for me) was that the training part of the teacher for both alternatives 
(joint and best response) was the teacher giving an example based on the goal and previous 
guess, then the student guessing, then the teacher giving an example based on the goal
and the previous guess, then the student guessing, etc.

# Can recurrent neural networks warp time?

Essentially consider a basic RNN, make it continuous, add the constrait that it must be able 
to learn functions under alternation of time. You don't know how time is warped, so learn that 
too. Discretize it. Then you get something closer to the gates in a GRU/LSTM.


# 18.702 (Self Study)

## Rings

An (unital) ring is a structure with two operations \\(+,\times\\), abelian group
on addition and a monoid under multiplication, with distributive law.
Morphisms are the obvious ones. Subobjects (subrings) are the obvious ones.
Basically fields without division.

For any ring \\(R\\) we can consider the polynomial ring \\(R[x]\\).
That is just the ring generated by freely adjoining \\(x\\). 
For any monoid \\(M\\), we can consider \\(R[M]\\)
with elements \\(\sum\_{m\in M} mr_m\\). This is clearly a ring.
We have that \\(R[x]\\) is basically just \\(R[\mathbb{Z}]\\). 
We have that \\(R[x_1,\ldots,x_k]\\) is basically just \\(R[\mathbb{Z}^k]\\).
Also basically just \\(R[\mathbb{Z}^{k-1}][\mathbb{Z}]\\), etc.

Note that \\(\mathbb{Z}\\) is initial. That is, for every ring \\(R\\),
there's an unique morphism \\(\mathbb{Z}\to R\\), given in the obvious way.
I would probably just ignore that result if I didn't knew about Category
Theory.

## Ideals

We say \\(I\\) is a left ideal if \\(\forall r\in R, i\in I, ri \in I\\)
and it's closed under addition. Right ideal is the other way. Ideal if both.

Note that kernels of morphisms are ideals. This is stronger than being a subring,
modulo the requirement of having one. It's a subrng, without the i, I guess.
A principal ideal is one generated by an element. That is, ideals of the form 
\\(xR\\) for some \\(x\\). This is a right ideal. If multiplication is commutative,
it's an ideal.

As always, we are interested in the question of decomposition. In groups we used normal
subgroups, in abelian in particular cyclic ones. Here we will use ideals.
We call a ring proper if the only ideals are the zero (generated by zero)
and the unit (generated by the unit, which is equal to the se itself).

Principal ideals, in a sense, encompass the idea of divisibility. The ideal generated
by a set of elements is the linear combinations of those elements. Ideals might need
a lot of elements (all?) to be generated.

Note that since nonzero elements of a field are invertible, every ideal is either
trivial or unital. Suppose a ring has only two ideals. It has to be the trivial and the 
unital, so \\(0\neq 1\\). Consider \\(aR\\). This has \\(a\\), so it contains every element,
in particular \\(1\\). So \\(a\\) has a (right) inverse. Thus the ring is a field.

Note that every ideal in \\(\mathbb{Z}\\) and \\(F[x]\\) for a field \\(F\\) 
is a principal ideal. Basically, it's the gcd of all the elements. 
That is, they are principal ideal domains.

## Quotient Rings

As expected, if we have an ideal \\(I\\) of \\(R\\), we can take the cosets over the addition.
There will be a canonical projection. They will form a ring. The kernel of the projection
will be the ideal \\(I\\). This motivates the definition of the ideal as the correct
notion for breaking groups.

In groups we had that normal subgroups and kernels were the same. Here we have that ideals 
and kernels are the same. Thus we can study one with the other. An again (and again and again)
there's a mapping property (and so on and so on). Same correspondence between subrings containing
kernel and subrings of domain.

Also note that taking quotients is commutative, in the following sense. If we have a ring \\(R\\)
and two elements, we have \\(R/(b)/(a)\cong R/(a,b)\cong R/(a)/(b)\\).

## Other

Adjoining elements:
How to construct \\(\mathbb{C}\\) from \\(\mathbb{R}\\)? Well, duh, the way we have always
done it, except change "imagine" for "do it". That is, we start with \\(\mathbb{R}\\). 
We can take the polynomials over the reals. Then we have that the imaginary number
\\(i\\) is such that \\(i^2 +1=0\\). So we quotient over it.
And that's that! \\(\mathbb{R}[x]/(x^2+1) \cong \mathbb{C}\\). This is a ring extension.

In general, a ring (or whatever) extension is just anything that flipping would be a subobject.
So the complex are an extension because the reals are a subobject.

The expected results apply.

Products are the expected ones, following the categorical product. If \\(e\\) is idempotent
(so \\(e^2 = e\\)), then a lot of obvious stuff happens buy in particular 
\\(R\cong eS \times (1-e)S\\).

An integral domain is one without zero divisors. We can construct fraction fields over
integral domains in the obvious way. Note it will still be a field of fractions,
and applying the construction again yields the same space.

## Maximal ideals

A maximal ideal is an ideal that is maximal (under the poset of inclusion).
Note that if we have a surjection \\(\phi : R\to F\\) from a ring to a field, then 
the kernel is an ideal. More over, we have that the ideals of the field are the zero and unital,
so there are two ideals that contain the kernel. These are exactly the kernel and the unital.
Hence the kernel is a maximal ideal.

We have that a kernel is a maximal ideal if and only if the domain is a field. 
Also if and only if the ring of cosets is a field. Trivially, the zero ideal is maximal
if and only if the ring is a field.

Maximal ideals connect with irreducibility. This makes sense, because if there were to be a 
bigger ideal, then taking cosets will reduce that bigger ideal into a nontrivial ideal.

We have that the maximal ideals of \\(\mathbb{C}[x_1,\ldots, x_n]\\) are in bijective
correspondence to the points of \\(\mathbb{C}^n\\). We take a point, consider the substitution
map to that point, the kenrel of that substitution map. That maps points to ideals.
This is maximal, since complex are a field. So maps points to maximal ideals.
On the other hand, if we have a maximal ideal, we can consider the canonical projection \\(\pi\\)
to it's posets, which will form a field. We can consider \\(\pi_i : \mathbb{C}[x_i]\to 
\mathbb{C}[x_1,\ldots,x_n]/M\\) the restriction to one variable. We see that the kernel of 
\\(\pi_i\\) has to be a maximal ideal since it's not zero. We have that \\(M\\)
contains this ideal, which is multiples of \\(x-a_i\\). Hence \\(M\\)
is generated by \\((x-a_1,\ldots, x-a_n)\\). Thus bijection.

## Algebraic geometry

We will be studying subsets of \\(\mathbb{C}^n\\) that are common roots of a set of polynomials.
Hence studying geometry in an algebraic way. We call such kind of subset an algebraic variety,
or a variety. Note that if we were to extend this to "infinite sets",
the varieties generated by a set would be the same as the ones generated by the ideal
generated by that set. Hence we can link varieties and (finitely generated) ideals.

The nullstellensatz tells us that the varieties generated by maximal ideals are the points.

Suppose we have an ideal \\(I\\) generated by \\(f_1,\ldots, f_k\\). This induces 
a field \\(\mathbb{C}[x_1,\ldots, x_k]/I\\). The maximal ideals of this field are in
bijection with the points in the variety of \\(f_1,\ldots, f_k\\).

Note that this is Hilber'ts when the set is empty. In a sense, this is hilbert modulo a
couple more sets. Note that maximal ideals in \\(\mathbb{C}[x_1,\ldots, x_k]/I\\)
are in correspondence to maximal ideals that contain \\(I\\). An ideal contains \\(I\\)
if and only if contains all the generators. Ideals of \\(\mathbb{C}[x_1,\ldots,x_k]\\)
are generated by substitution maps. Hence maximal ideals that contain \\(I\\)
are kernels of substitution maps that contain \\(I\\). A substitution map contains \\(I\\)
if under every element of \\(I\\), the point is zero. Hence the point is in the variety.

So point in variety iff substitution map contains polynomials iff substitution map kernel
contains ideal generated of polynomials iff is maximal ideal that contais ideal
generated of polynomials.

Modulo infinite procedure, (almost) every ring has a maximal ideal. 
Suppose you have that a set of polynomials has no mutual solution. Then their variety is empty.
So it has no maximal ideals. Hence the linear combination has to be unital or zero.
Since it isnt' zero, its unital. In particular, one of those linear combination is the identity.

In \\(\mathbb{C}^2\\), varieties over two variables have either a common constant factor, or 
finite points. Hence most interesting things happen as locus of one point.

# Chapter 0

## Ideals

Take a subgroup \\((I,+)\\) of \\((R,+)\\). By abelianness, we can take the quotient
and get a subgroup \\((R/I,+)\\). When can this be extended to a subring.
What do we want? We want \\(\pi(a)\pi(b) = ab + aI + bI + I^2 =ab+(a+b+1)I\\), and you want
this to be equal to \\(\pi(ab) = ab + I\\). Hence we want \\((a+b)I\\) to kinda
disappear. Taking \\(b = -1\\), we get that we want \\(aI = I\\). It's clear to see that 
this is the only required thing.

We can now make the normal decompositions with kernel and images of maps. 
In particular, if \\(\phi : R\to S\\), then \\(S\cong \frac{R}{\ker \phi}\\).
We also have the fraction cancelation thing.

If we have that \\(\\{I\_\alpha\\}\_{\alpha\in A}\\), then the sum is an ideal.
In particular \\((a_1,\ldots, a_n) = (a_1)+\ldots + (a_n)\\).
A finitely generated ring is called noetherian. Principal ideal domains
are noetherian domains. 

We have that \\(I\\) is a prime ideal if R/I is an integral domain.
Equivalently \\(ab\in I\\), then \\(a\in I\\) or \\(b\in I\\). 

Consider a commutative ring \\(R\\) and an ideal \\(I\\). 
If the quotient is finite, the ideal is finite if and only if it's maximal.
If \\(R\\) is a principal ideal domain, and \\(I\\) is a nonzero ideal,
then it's prime if and only it's maximal.

The set of prime ideals of a commutative ring is called the spectrum of the ring.
For example, the spectrum of \\(\mathbb{Z}\\) are basically the prime numbers,
and the zero. The spectrum of \\(\mathbb{C}[x]\\) is the plane and the zero (generated ideals).
The krull dimension is the longest chain of prime ideals, and for PIDs they have dimension one.
So they correspond to curves.

## Modules

Rings have the annoying problem that they have to be quotiented by almost but not quite rings,
unlike groups, abelian or not. We will use modules to fix this. For a ring \\(R\\),
ideals, the ring, and quotients are modules over \\(R\\). Kernels, cokernels exist and they
are nice. You can think abelian groups as modules over the integers. Vector spaces
will be modules over fields.

We have that a (left)-\\(R\\)-module \\(V\\) has an operation \\(\sigma : R\times V\to V\\)
that works in the usual way of \\(\sigma(xy,t)=\sigma(x,\sigma(y,t))\\), and others. 
So basically \\(R\\) acts on \\(V\\) in a nice way.
Alternatively, we can see this as a morphism of rings \\(R\to End\_{Ab}(M)\\),
where we think \\(End\_{Ab}(M)\\) as a ring.

What would be the homomorphism? Since a module is a map, it should basically be a natural 
transformation. Hence it's a morphism of abelian groups that is compatible with everything.
Hence \\(R\\)-modules form a category.

Given a morphism \\(\alpha : R\to S\\), we can define a morphims \\((r,s)\mapsto \alpha( r)s\\).
This is a clear module. If \\(R\\) is commutative, and the morphism maps to the center,
we hvae that \\((r_1s_1)(r_2s_2) = \alpha(r_1)s_1\alpha(r_2)s_2 = \alpha(r_1)\alpha(r_2)s_1s_2
=\alpha(r_1r_2)s_1s_2=(r_1r_2)(s_1s_2)\\).

If this happens, it's called an \\(R\\)-algebra (this meaning commutative and inside center).
These form a category, and \\(\mathbb{Z}-Alg\\) are rings. Then you can do the typical
stuff of subobjects, quotients, breaking morphisms, etc.