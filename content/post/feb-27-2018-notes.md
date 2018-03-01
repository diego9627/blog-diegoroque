---
title: "Feb 27 2018 Notes"
date: 2018-02-27T09:40:46-05:00
draft: false
tags: ["18.175", "AI Mathematician UROP", "ML", "18.408", "18.615"]
---

Three modes of convergence,

1. Pointwise \\(P(\lim\_{n\to \infty} \xi_n(x) = \xi(x)) = 1\\)
2. Probability \\(\forall \varepsilon > 0\\), we have 
\\(\lim\_{n\to\infty} P(|\xi_n(x) - \xi(x)| < \varepsilon) = 1 \\)
3. Distribution, for \\(F\_{\chi}(x) = P[\chi \leq x]\\),
we have \\(F\_{\xi_n}(x) \to F\_{\xi}(x)\\) for every point where \\(F\_{\xi}\\)
where it is continuous.


Proposition: \\(\xi_n\to \xi\\) in distribution if and only if
for each continouus bounded \\(f\\), we have \\(E[f(\xi_n)]\to E[f(\xi)]\\).

Only if: Taking the indicator \\(I_x = y\mapsto I_{y\leq x}\\) would give us what we want, except that 
it wouldn't be continuous. So we fix that. 
Fix \\(x\\) for now. For \\(\varepsilon > 0\\), consider \\(g_{\varepsilon}(x)\\) 
is the indicator we want below \\(x - \varepsilon\\) and above \\(x\\). It is clear that 
\\(I_x \geq g\_{\varepsilon} \geq I\_{x - \varepsilon}\\). Taking limits, we get 
(one side) of what we want. Do it the other side, and we get that for continuous points,
we get the convergence.

If: Note that the cummulative functions are continuous everywhere but a coutnable number of points. Let \\(f\\) be a continuous function bounded by \\(C\\).
Let \\(\delta > 0\\). Then there exists \\(A > 0\\), such that \\(F\_{\xi} < \delta,
1- F_{\xi} < \delta\\), and \\(A\\) is a point of continuity.

Note that the outside interval of \\([-A,A]\\) has very little density, by boundedness 
less than \\(2\delta C\\). Hence we can limit ourselves to inside the interval.

Partition \\([-A,A]\\) into \\(N\\) parts for big enough \\(N\\) into 
\\([-A=x_0,x_1,\ldots, x_N=A]\\), such that inside one small interval it is bounded by 
\\(\delta\\).

We would then take a discrete integral, bound everything by \\(O(\delta)\\).
Taking \\(\delta \to 0\\) we get convergence.

4. \\(L_1\\) convergence, in expectation. We have \\(E|\xi_n - \xi| \to 0\\).


Egorov's theorem. If \\(f_n\\) converge pointwise to \\(f\\), then there exist arbitrarily 
large sets (in the sense of \\(\forall \varepsilon, \exists A, A^c < \varepsilon\\))
such that in \\(A\\), it converges uniformly.

# 18.615 

Starting writting the two psets. 

# 18.408

Last time we were moving spectral graphs to random walks. Let the spectral gap is 
\\(\lambda = 1 - \mu_2^{\prime}\\). We get 

$$ \lVert p_t  - \pi\rVert_2 \leq \left(1 - \lambda\right)^t \sqrt{\frac{\max_x d(x)}{\min_y d(y)}} $$

we also have an $l1$ bound for any $v$

$$ \lVert p_t(v)  - \pi(v)\rVert_1 \leq \left(1 - \lambda\right)^t \sqrt{\frac{d(v)}{\min_y d(y)}} $$

Cheeger's inequality now becomes

$$ \frac{\Phi^2}{2} \leq \frac{1 - \mu^{\prime}_2}{2} = \frac{\lambda}{2} = \leq 2\Phi(G) $$

so \\( \Phi(G) \\) is related to the rate of convergence. Bounds in \\(\Phi\\) has to do with 
mixing in a tight way. This is natural, because of clusering information.

## Chernovs bound

Everyone's favourite example:

Compute \\(\pi \\) by throwing darts at a dartboard. Count number of random points in 
circle inside square.
Total probability is \\(\frac{\pi}{4}\\). If we want an algoritm, we also want 
something reasonable.

Question: How close is this to the actual bound?

We will check qualitative multiplicative bounds. 

Chernoff: The probability \\(R\\) fails to \\(\varepsilon\\)-aproximate \\(E[R]\\)
is 

$$ P(|R - E[R]|\geq \varepsilon E[R]) \leq 2^{-\Theta(1)np\varepsilon^2} 
= 2e^{-\Theta(1)E[R]\varepsilon^2}$$

Notes:

* Pretty tight
* Needs indepdendence trials
* Multiplicative error, not additive
* For fixed \\(\varepsilon\\), falls off exponentially in \\(n\\)
* Smaller \\(\varepsilon\\) needs more trials.

If you want an \\(\\varepsilon\\)-approximation with probability \\(1-\delta \\) , you need

$$ N\geq \Theta\left(\frac{\log\left(\frac{1}{\delta}\right)}{\varepsilon}\right) $$

In words: Need enough trials to get 
 \\( \Theta\left(\frac{\log\left(\frac{1}{\delta}\right)}{\varepsilon}\right) \\)
 successes in expectation.

Easy to make \\(\delta\\) smaller, harder to make \\(\varepsilon\\) smaller.

WHen problems?

* Bad at darts: Big dartboard, small circle
* Bad at throwing darts

An \\((\varepsilon,\delta)\\) approximation scheme is an algorithm to compute a 
\\(\varepsilon\\)-approximation with probability \\(1-\delta\\).

A fully polynomial-time approximation scheme (FPTAS) 
is an algorithm such that it is \\(
    poly(n,\frac{1}{\varepsilon},\log\left(\frac{1}{\delta}\right))\\).

## Nontrivail exaple: DNF solutions

Count DNF solutions. Not much more to it.

How not ot do it: randomly asign \\(0,1\\), repeat \\(k\\) times.

Idea: Importance samplign: change your probability to get a distribution
with higher likelyhood to be good.

## Permanent

Like a determinant without the signs. Turns out that this is sharp P hard,
while the determinant is poylnomial.

Consider when all entries are 0,1. Still shapr P hard!

We can interpret this as the number of perfect matchings in a bipartite graph,
viewing the matrix as an incidence matrix.

Why this is weird? Sharp P was defined as counting of hard problems,
but perfect matching is easy, and this is counting of easy then.

Surprising: Even thought it's sharp P hard, it has a FPTAS.

We are going to prove it for dense graphs, with each vertex degree 
at least \\(\frac{n}{2}\\). (Proven in 1989). Still sharp p complete.

In 2001, it was shown for arbitrary graphs, hence for any matrix with 
nonnegative entries.

## What won't work:

* Any naive MC, like guessing a permutation and see if it matches
* Others

## General Strategy

Will look at all possibly partial matchings, not only perfect ones. Let \\(M_k\\)
be the matchings with size \\(k\\).

Suppose we could sample from \\(M_k\cup M\_{k-1}\\), for any \\(k\\).

# ML

Read [attention and augmented neural networks](https://distill.pub/2016/augmented-rnns/).

In Deep Learning, the trick is to make everything differentiable.

Neural Turing Machine: Memory is discrete. Make it differentiable by distributing attention
between then, then reading a weighted sum or writting to all in a weighted manner.

How to focus? Like we normally focus in machines: by content and by location.

Attentional interfaces: Have a second network focus on the first network, but with particular 
attention to some parts. "Attentional interfaces can be used whenever one wants to interface
with a neural network with repeated structure in its output". Seems like it is particularly
good for composiiton.

Adaptive computation time: Roughly, we want to spend more time in hard stuff and less time 
in easy stuff. Again, same problem of steps not being differentiable, and same 
solution of just making it differentiable by bolting a probability distribution on top.
So repeat steps, and outout is weigted combination. Basically, keep the RNN stuff but
repeat an output if it's "hard".

Neural programmer: make the NN interface with a language. "it learns to genearate code for a task
(...) without needing examples of correct programs". Blablabla not differentaible blablabla
blablbla make it differentiable with probabilities.
So the output is a probability distribution of what's the next step.

So how do you run a program consisting of distribution of operations? Well, the obvious way,
actually. Just run it all at the same time and average it. Except that this is too annoying
to actually code properly, so just run it sequentially, average it per step, and 
get the "canonical" answer for a step.

It even allows types!

"A human with a piece of paper is, in some sense, much smarter than a human without.
A human with mathematical notation can solve problems they otherwise couldn’t."

Interaction between human intuition and formalism, then bring this to computers. In a sense,
Neural Networks are "intuition" of computers, and almost everything else has been formalism.

Reinforcement is about learning on one action, attention is about learning on forked actions.

# AI Mathematician UROP

Read a bunch of papers:

## Learning to Compose Neural Netowrks for Question Answering

Highlights: Composable. Attention.

Neural modules look like Neural Turing Machine/Neural Programmer, but instead of using 
"crisp" functions, it uses NN/ML. Here's there's an analogy with people also using fuzzy 
skills (recognizing where's a bird) and not only crisp skills (adding), when breaking 
questions.

Each word is attached a particular instanciated module, then the question is translated
into (several) tree structures, then attention/NTM over them and input.

Experimental results are "state-of-the-art". Note that this is kind of a general approach.

The core idea would be NTM but with neural modules (that are jointly trained).

## Deep Compositional Question Answering with Neural Module Networks

Essentially the same as the previous one??? But it focuses in a different set of 
neural modules, more towards answering questions about pictures. Here it is mainly a refinement
of the previous paper to use those kind of modules. 

## Inferring and Executing Programs for Visual Reasoning


## Learning Knowledge Base Inference with Neural Theorem Provers

## Programming with a Differentiable Forth Interpreter

## End-to-End Differentiable Theorem Proving

## Machine Learning of **Coq** Proof guidance: First Experiments

## Holophrasm: a neural Automated Theorem Prover for higher-order logic

## Proof Mining with Dependent Types

## HOLStep: A Machine Learning Dataset for Higher-Order Logic Theorem Proving

## From Gameplay To Symbolic Reasoning: Learning SAT Solver Heuristics in the Style of Alpha(Go)Zero

Exactly what it says on the tin. SAT is the game. Expanding is step. 
Getting instance/Disproving is winning. Play!