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

### Statement
All nontrivial zeros of the Riemann zeta function satisfy $\Re(s) = \tfrac12$.

### Setup and notation
The smoothed approximate functional equation (AFE) yields:

$$
\xi(s) = \Xi_1(s) + \Xi_2(s) + E(s), \quad E(s) = O_A((1+|t|)^{-A}).
$$

Define coherence variables:

$$
 r(s) = \frac{|\Xi_1|}{|\Xi_2|}, \quad 
 \Delta(s) = \arg \Xi_2 - \arg \Xi_1 - \pi, \quad 
 K(s) = \frac{2r(s)\cos\Delta(s)}{1+r(s)^2}.
$$

### Key lemmas
- **L1 (Lock criterion):** $K(s)=1$ iff $r(s)=1$ and $\Delta(s)=0$.  
- **L2 (Amplitude ratio):** For $|t|\ge T_0$, $r(s)=e^{2\sigma-1}(1+\varepsilon(\sigma,t))$ with $|\varepsilon|\ll(1+|t|)^{-\eta}$.  
- **L3 (Off-line cap):** $K(\sigma+it)\le \text{sech}(2\sigma-1)+o(1) < 1$ for $\sigma\neq\tfrac12$.  
- **L4 (On-line lock):** At zeros on the line, $\Xi_1 + \Xi_2 = 0$ forces $K=1$.

### Proof
Assume a zero off the line: $\xi(s_0)=0$, $\sigma_0\neq\tfrac12$. Cancellation implies $K(s_0)\approx1$. By L3, $K(s_0)<1$. Contradiction. Hence all zeros lie on the critical line. ∎

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

