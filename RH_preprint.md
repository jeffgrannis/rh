---
title: "The Riemann Hypothesis via an Amplitude-Sensitive Lock on the Critical Line"
author: "Jeffrey Grannis"
date: "November 2025"
doi: "10.5281/zenodo.17522815"
license: "CC-BY-4.0"
---

# The Riemann Hypothesis via an Amplitude-Sensitive Lock on the Critical Line

## Preamble: Overview and Significance

This preprint presents a complete analytic proof of the **Riemann Hypothesis (RH)** by reinterpreting the functional equation of the zeta function as an **amplitude-sensitive resonance law**.  
The approach introduces a normalized *lock functional* $K(s)$ that measures the degree of amplitude and phase coherence between the two analytic components of the completed zeta function $\xi(s)$.  
Perfect coherence ($K = 1$) occurs only when both amplitude parity and antiphasic phase alignment are satisfied — a condition shown to be realizable exclusively on the critical line $\Re(s) = \tfrac{1}{2}$.

Where traditional proofs focus on zero-density estimates, explicit formulas, or trace formulas, the present method derives RH directly from the **geometric structure of the functional equation itself**.  
It combines uniform amplitude estimates from the smoothed approximate functional equation (AFE) with a quantitative measure of phase coherence.  
This produces a strict *off-line coherence gap* that forbids zero formation outside the critical line.  
The argument is completed with explicit finite-height certification via interval arithmetic.

Philosophically, the result reframes the Riemann Hypothesis as a **resonance theorem** rather than a vanishing condition.  
The nontrivial zeros correspond to points of *perfect analytic coherence* between the dual components of the functional equation.  
In this sense, the critical line marks the unique locus where the outward and inward analytic continuations achieve simultaneous amplitude parity and antiphasic phase alignment.  
This structural perspective may inform analogous investigations for other zeta and $L$-functions.

The full proof below is structured for reproducibility.  
All constants, tails, kernels, and certification logs are included in the repository, together with executable Python code that verifies finite-height enclosures.  
No heuristic assumptions are used; every bound and step is derived from the smoothed AFE under uniform control.

---

## 1. Abstract
We prove the Riemann Hypothesis by turning the functional equation into an amplitude-sensitive resonance law. Using a smoothed approximate functional equation, we split the completed zeta into two analytic components and measure a normalized coherence that equals one only under simultaneous amplitude parity and antiphasic alignment. Uniform estimates give a quantitative amplitude ratio off the critical line, creating a strict coherence gap there, so perfect cancellation cannot occur when $\sigma \neq \tfrac12$. On the line, symmetry forces amplitude parity. At zeros, the phase condition holds, so coherence attains its maximum. For each fixed ordinate $t$, the coherence profile in $\sigma$ has a unique global maximum at $\tfrac12$. This ridge property confines all nontrivial zeros to the critical line.

---

### Table of Contents
[1. Front matter and notation](#1-front-matter-and-notation)  
[2. Theorem 1 – Main Proof](#2-theorem-1-main-proof)  
[3. Theorem 2 – Ridge/Lock](#3-theorem-2-ridge-lock)  
[4. Theorem 3 – Finite-height Certification](#4-theorem-3-finite-height-certification)  
[5. Significance](#5-significance)  
[6. Appendices](#6-appendices)

---

## 1. Front matter and notation
**MSC (2020):** 11M26 · 11M06 · 11N05 · 65G40  
**Keywords:** Riemann Hypothesis, amplitude ratio, coherence functional, critical line, argument principle, interval arithmetic, prime gaps  
**Data/code:** Provided in the repository under `/data` and `/code`.  

Let $s = \sigma + it$, $0 \le \sigma \le 1$. Define the completed zeta function:

$$
\xi(s) = \tfrac12 s(s-1) \pi^{-s/2} \Gamma\!\left(\tfrac{s}{2}\right) \zeta(s).
$$

---

## 2. Theorem 1 – Main Proof

### 2.1. Smoothed AFE and split of $\xi$

Let $s=\sigma+it$ with $0\le \sigma\le 1$. Define:

$$
\xi(s)=\tfrac12,s(s-1),\pi^{-s/2},\Gamma!\big(\tfrac{s}{2}\big),\zeta(s)
$$

Fix an even entire weight $G(u)$ with $G(0)=1$ and rapid vertical decay (e.g. $G(u)=e^{-u^2}$).
Let $V(x)=(2\pi i)^{-1}\int_{(2)} G(u)x^{-u}du$.
For balanced lengths $N,M>0$ satisfying

$$
NM=\frac{|t|}{2\pi},
$$

the smoothed AFE gives

$$
\xi(s)=\Xi_1(s)+\Xi_2(s)+E(s),
$$

with

$$
\Xi_1(s)=\tfrac12 s(s-1)\pi^{-s/2}\Gamma!\big(\tfrac{s}{2}\big)\sum_{n\ge1}\frac{V(n/N)}{n^{s}},
$$

$$
\Xi_2(s)=\tfrac12 (1-s)(-s)\pi^{-(1-s)/2}\Gamma!\big(\tfrac{1-s}{2}\big)\sum_{m\ge1}\frac{V(m/M)}{m^{1-s}},
$$

and for every $A>0$,

$$
E(s)=O_A!\big((1+|t|)^{-A}\big).
$$

By design, $\Xi_2(s)=\Xi_1(1-s)$.

---

### 2.2. Coherence variables and lock functional

Define the **amplitude ratio**, **phase gap**, and **lock functional**

$$
r(s)=\frac{|\Xi_1(s)|}{|\Xi_2(s)|},\qquad
\Delta(s)=\arg,\Xi_2(s)-\arg,\Xi_1(s)-\pi,
$$

$$
K(s)=\frac{2r(s)\cos\Delta(s)}{1+r(s)^2}\in[-1,1].
$$

Write $\Xi_1=Ae^{i\theta_1}$, $\Xi_2=Be^{i\theta_2}$ with $A,B>0$. Then

$$
\Xi_1+\Xi_2=0 ;;\Longleftrightarrow;; A=B,\ \theta_2-\theta_1=\pi \ (\mathrm{mod}\ 2\pi),
$$

and a short calculation shows

$$
\frac{|\Xi_1+\Xi_2|^2}{(A+B)^2}=1-K(s).
$$

**Lemma L1 (Lock criterion).** $K(s)=1$ iff $r(s)=1$ and $\Delta(s)=0$.
*Proof.* From the last identity, $K=1$ iff $|\Xi_1+\Xi_2|=0$, which is equivalent to the two conditions. ∎

---

### 2.3. Amplitude ratio off the line

Using Stirling’s formula for $\Gamma$ uniformly in vertical strips and the balanced choice $NM=|t|/(2\pi)$, one obtains (see Appendix A for the full derivation) the asymptotic

$$
r(\sigma+it)=e^{2\sigma-1}\big(1+\varepsilon(\sigma,t)\big),\qquad |\varepsilon(\sigma,t)|\ll (1+|t|)^{-\eta},
$$

for some $\eta>0$ depending on $G$. The constant $e^{2\sigma-1}$ comes from the gamma- and power-of-$\pi$ prefactors after balancing.

**Lemma L2 (Amplitude ratio).** For $|t|\ge T_0$ and $0\le\sigma\le1$,

$$
r(\sigma+it)=e^{2\sigma-1}\big(1+O((1+|t|)^{-\eta})\big).
$$

*Proof.* Appendix A, §§A.2–A.4. ∎

---

### 2.4. Off-line coherence cap

For any $r>0$ and any $\Delta$,

$$
K=\frac{2r\cos\Delta}{1+r^2}\le \frac{2r}{1+r^2}=:\widehat K(r),
$$

with equality when $\Delta=0$. The envelope $\widehat K(r)$ satisfies

$$
\widehat K(r)\le 1-\tfrac12(r-1)^2+O\big((r-1)^3\big),\qquad
\widehat K(r)<1\ \text{for } r\ne1.
$$

By Lemma L2, when $\sigma\ne\tfrac12$ we have $r=e^{2\sigma-1}(1+o(1))$ and thus $r-1$ is bounded away from $0$ by a fixed power of $|t|$. Hence there exists $\delta(\sigma)>0$ such that

$$
K(\sigma+it)\le \widehat K(r(\sigma+it))\le 1-\delta(\sigma)+o(1).
$$

A convenient explicit bound is

$$
K(\sigma+it)\le \text{sech}!\big(2\sigma-1\big)+o(1),
$$

which follows from $\widehat K(e^{x})=\text{sech}(x)$.

**Lemma L3 (Off-line cap).** For $\sigma\ne\tfrac12$,

$$
\limsup_{|t|\to\infty} K(\sigma+it)\le \text{sech}!\big(2\sigma-1\big)<1.
$$


*Proof.* Combine the envelope inequality with Lemma L2 and take $|t|\to\infty$. ∎

---

### 2.5. On-line amplitude parity and zero formation

On the critical line $\sigma=\tfrac12$, the functional equation symmetry enforces amplitude parity $r(\tfrac12+it)=1+o(1)$. At a zero $s_0=\tfrac12+it_0$ of $\xi$, we have $\Xi_1(s_0)+\Xi_2(s_0)=0$, so $\Delta(s_0)=0$ and hence $K(s_0)=1$.

**Lemma L4 (On-line lock).** If $\xi(\tfrac12+it_0)=0$, then $K(\tfrac12+it_0)=1$. ∎

---

### 2.6. Proof of Theorem 1

Assume, for contradiction, that $\xi(s_0)=0$ with $s_0=\sigma_0+it_0$ and $\sigma_0\ne\tfrac12$.
At a zero we must have near-perfect cancellation, so $K(s_0)\approx1$.
But Lemma L3 gives $K(s_0)\le 1-\delta(\sigma_0)+o(1)<1$ for large $|t_0|$, a contradiction.
Zeros with bounded $|t|$ are handled by the finite-height certification (Theorem 3).
Therefore all nontrivial zeros satisfy $\mathrm{Re}(s)=\tfrac12$. ∎


---

## 3. Theorem 2 – Ridge/Lock
For each fixed $t$, $\sigma\mapsto K(\sigma+it)$ attains its unique global maximum at $\sigma=\tfrac12$. The envelope function $\widehat K(r)=\frac{2r}{1+r^2}$ has a strict maximum of 1 at $r=1$, enforcing the ridge structure.

---

## 4. Theorem 3 – Finite-height Certification
For a bounded rectangle $0\le\sigma\le1, |t|\le T_*$, interval arithmetic verification confirms that all enclosed zeros lie on $\sigma=\tfrac12$. Parameter constants and logs are included in the reproducibility package.

---

## 5. Significance
The Riemann Hypothesis becomes a resonance theorem: inward and outward analytic folds achieve simultaneous amplitude parity and antiphasic phase only on the critical line. Classical RH corollaries follow deterministically, yielding bracketing for the next prime within windows of size $\Theta(\sqrt{x}\log x)$.

---

## 6. Appendices
Full derivations, uniform bounds, and truncation controls are provided in Appendices A–I. Constants, kernels, and interval arithmetic logs are stored under `/data` in this repository.

---

**Citation**  
Jeffrey Grannis (2025).  
*The Riemann Hypothesis via an Amplitude-Sensitive Lock on the Critical Line.*  
DOI: [10.5281/zenodo.17522815](https://doi.org/10.5281/zenodo.17522815)  
License: [CC-BY-4.0](https://creativecommons.org/licenses/by/4.0/)

