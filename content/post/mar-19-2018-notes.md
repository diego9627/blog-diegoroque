---
title: "Mar 19 2018 Notes"
date: 2018-03-19T09:34:39-04:00
draft: false
tags: ["18.S996"]
---

# Social Choice and Social Networks

No relation to Condorcet. Instead, Models of Competition / Coexistence on networks.
"Translate Berkley to Boston and cellphones to cryptocoins".

THis is a possible way to think about product adoption. 

Main question: Given this model of product adoption, what will happen to competing companies?

Example of a fun research problem: you come up with a fun question like that and try to model it 
mathematically.

(Similar to Chinese restaurant process?)

Model: Random graph model, linear preferential attachment model. 

Start with some graph $G_0 = (V_0, E_0)$. At each step, add a new onde, add $m$ edegs from 
new node to existing nodes. Edges chosen according to linear preferential attachment,
that is, proportional to the degree.

Type adoption: Extra laye on top of preferential attachment dynamics. Every node has a 
type/color, out of $N$ possible. When added to graph, node gets tipe. 
Probability of getting particular type with a probability distribution 
parametrized on number of neighbors of each type.

Parameteres: 

* $m$
* $G_0 = (V_0,E_0)$
* $(p_u^i)_{u,i}$

Examples of $p$: Linear model. Plurality. Don't listen, pick randomly. Or anything.

Results: When linear, it's supported on $[0,1]$. When not, on the roots of a polynomial. 

TODO: Add more to this