---
title: "Feb 23 2018 Notes"
date: 2018-02-23T11:06:06-05:00
draft: false
tags: ["18.702", "PLV Lunch", "Categorical Logic", "AI Mathematician UROP"]
---

# 18.702

Something about how a lot of the problems become clear when considering the geometry of them,
and happens a lot in commutative algebra.

We ahve that there's an evaluation map \\(ev_p : \mathbb{C}[x,y]\to \mathbb{C}\\)
where \\(p\in \mathbb{C}^2\\). This is an homomorphism.

Consider \\(\\{f\in \mathbb{C}[x,y] | f(p) = 0\\} = m_p\\) (thus the kernel). Observations:

* \\(f,g\in m_p\\) then \\((f+g)(p) = f(p)+g(p)=0\\) so \\(f+g\in m_p\\). 
This set is closed under addition.
* \\(f\in m_p, g\in \mathbb{C}[x,y]\\), then \\((fg)(p)=f(p)g(p) = 0\\) so \\(fg\in m_p\\).

More generally, let \\(S\subset \mathbb{C}^{2}\\) be any subset. We can generalize it 
from any single point to vanishing in every point. Call this set \\(I_S\\).
It has those properties, closure under addition and absorbing.

You can generlize it, considering the ring of convergent functions in a neighborhood of
\\((0,0)\\) in \\(\mathbb{C}\\). Then you consider the set of vanishing points on a 
particular subset. Then the same thing happens.

This is an ideal. That is, for any commutative ring, an ideal \\(I\\) is a subgroup
of the additive group, and absorbs multiplication. (Or we will see equivalently, it's a 
kernel of a homomorphism, like in the first case).

These are the things we want to take the quotient of this. We can see this because 
if we were to take a quotient of \\(R\\), then we definitely want to take it of the additive 
group. Any subgroup is a normal group, so at least we can take the quotient in that part.
But to take it on the other part, we will realize that we want \\(gI\subset I\\) for
every \\(g\in R\\).

Alternatively, quotienting is just taking the image of a surjective map. So if we relabel
everything and get a few properties, we get the same result.

As always, there's a canoncial map. 

Example: Let \\(S = \\{y = x^2\\}\\). What is \\(\mathbb{C}[x,y]/I_S\\)?
(Essentially \\(\mathbb{C}[x,y]\\) modulo \\(x^2 - y\\))
Well, this is isomorphic to \\(\mathbb{C}[z]\\) (getting new variable bc clearlness).

Symbollically, we see that we want \\(y\\) to be \\(x^2\\). We can construct the isomorphism
by mapping \\(x\mapsto z, y \mapsto z^2\\) and extending. We have a morphism
is injective if the kernel is trivial. By definition, this is only \\(I_S\\) so yeah.

# Categorical Logic 

TODO (But actually ... )

# PLV Lunch

Talk about POPL. Check link [here](https://docs.google.com/document/d/1WoY-h-Czcn5pPJRrjjUKupOhSQarqQkg_KXSGaxWN84/edit)

# AI Mathematician UROP

Check notion.so. Talked about Program Induction by Rationale Generation: Learning to Solve and Explain Algebraic Word Problems, DeepMath - Deep Sequence Models for Premise (and follow up), a bit for Interpretable and Pedagogical Examples.

Idea of turking significance for math to get values. Kind of in the idea of [this](https://blog.openai.com/deep-reinforcement-learning-from-human-preferences/).

Should also start reading about game semantics.