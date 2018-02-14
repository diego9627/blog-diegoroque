---
title: "Feb 13 2018 Notes"
date: 2018-02-13T11:49:02-05:00
draft: false
tags: ["Chapter0", "PL/SE Lunch","18.408", "UROP"]
---

# Chapter 0

If \\(R\\) is a ring, a left ideal is a subgroup \\((I,+)\\) of \\((R,+)\\)
such that \\(RI = I\\). So \\(I\\) is stable under left multiplication.
Ditto with right. Two sided is two sided. 

# PL/SE Lunch

Nothing.

# 18.408

## Quotient stuff patn and cycle

The path graph: Realize \\(P_n\\) as a quotient of \\(R\_{2n}\\) using 
\\(\pi:R\_{2n}\to P_n\\) by \\(\pi(i) = i\\) or \\(\pi(i) = 2n+1-i\\).

For any \\(G\\), we have \\(\[L\_Gx\](u) = \sum (x(u) - x(v))\\).

## Products of graphs and laplacians

Graph products: Product in category of graphs. Set of vertices is the product
in sets, and edges are the minimum necessary for commutation. So
\\((v\_1,w)\sim (v\_2, s)\\) and \\((v,w_1)\sim (v, w_2)\\).

Turns out \\(L\_{G\times H} = L_G \otimes I\_{H} + I\_{H}\otimes L_G\\). 
This ought to have a name, because is chain-rule looking and is generally 
reasonable, but I don't know one.

If \\(L_G\\) has eigenvalues and eigenvectors \\(\\{\lambda_i, x_i\\}_i\\)
and \\(L_H\\) has \\(\\{\nu_j , y_j\\}_j\\).

Then \\(L_{G\times H}\\) has eigenvalues and eigenvectors \\(\\{\lambda_i+\nu_j,
x_i\otimes y_j\\}\_{i,j}\\).

## Why Laplacian?

One dimensionally,  the laplacian is the sum of second partial derivatives. The 
claim is that the matrix laplacian is the discretization of the laplacian.

Consider the discrete derivatives. First (w/o scaling), the derivative is
\\(f(i+1) - f(i)\\). Second is \\(f(i+1)-2f(i)+f(i-1) = (f(k-1)+f(k+1))-2f(k)\\),
which is roughly incidence minus degree.

In general, N-th dimensional we get the laplacian of summing neighbors
and substracting degree.

$$L = \nabla\_{n\times m}^T\nabla\_{m\times n}$$

You in general can use the matrix laplacian wherever you would use the laplacian 
operator. There's a fairly close 1-1 analogy between spectral theory vs 
harmonic analysis. Since you don't have limits and can't eliminate boundaries,
the theorems will be basically the same but uglier when moving from harmonic
to spectral.

Path and lines had eigenvectors that look like fourier coefficients.

## Bounds

$$\sum \lambda_i \leq \deg\_{\max}n$$
Proof: trace of L

$$\lambda_2 \leq \frac{\sum \deg(i)}{n-1}$$
$$\lambda_n\geq  \frac{\sum \deg(i)}{n-1}$$
Proof: Previous and \\(\lambda_1=0\\)


# UROP

Nothing except expectancy to work more.

# DRP

Continue with Chapter 4 exercises. 
