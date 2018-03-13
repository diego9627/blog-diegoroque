---
title: "Mar 12 2018 Notes"
date: 2018-03-12T09:35:15-04:00
draft: true
tags: ["18.S996"]
---


# Bayesian Group decisions, algorithm and complexity

Manue:

1. Notation, model, problem
2. SUBSET-SUM Reduction
3. EXACT-COVER Reducation
4. Transparent Structures
5. Iterated Eliminations
6. Transitive Structures

1-4 beliefs
5-6 actions

Model:

Initial private signals \\(s_i \in S_i, i \in [n]\\).
At time zero

$$ \mu\_{i,0}(\theta) = \frac{P\_{\theta}(s_i)v(\theta)}{\sum\_{\theta} P\_{\theta}(s_i)v(\theta) }$$

$$I\_{i,t} \subset S_1 \times S_2\times \cdots \times S_n$$

the set of feasible signal profiles at time $t$ for agent $i$

$$ I\_{i,0} = s_i \times \prod\_{J\neq i} S_J$$
$$ I\_{i,1} = s_i \times \prod\_{J\in N)i} S\_{J,0}  \times \prod\_{J\neq i} S_J$$

We have \\(I\_{i,t} \subset I\_{i, t-1}\\).


$$ \theta = \\{0,1\\} $$

$$ \Phi\_{i,t} = \log \frac{\mu\_{i,t}(1)}{\mu\_{i,t}(0)} $$

$$ \lambda_i = \log \frac{P_i(s_i)}{P_0(s_i)} \forall s_i \in S_i$$

$$ \gamma = \log \frac{v(1)}{v(0)} = 0$$ uniform prior \\(v(1) = v(0)\\)

Problem (group decision):

At any time \\(t\\), given graph \\(G\\):

private signals \\(s_i\\), history of neighboring beliefs \\(\mu\_{J,N}\\), \\(J\in N_i,
\tau = 1,\ldots , t-1\\).

Determine bayesian posterior \\(\mu\_{i,t}\\).

Reduction just means reduction in the NP/complexity setting.
