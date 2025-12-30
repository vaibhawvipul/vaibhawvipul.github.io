---
layout: post
title: "The Shared State of Mathematics"
date: 2025-12-30
author: "Vipul Vaibhaw"
---

Ending this year with a small reflection on my advance math journey so far...

**On the hidden unity beneath complex analysis, number theory, and geometry**

Last month I wrote about [failed attempt to understand Fermat's Last Theorem](https://vaibhawvipul.github.io/2025/11/25/I-tried-to-understand-FLT.html). I confessed failure — or at least, incomplete success. I understood the skeleton of Wiles' proof, but not its flesh.
But something unplanned happened, I stumbled into something I wasn't looking for: a hidden architecture beneath mathematics itself.

Modular Forms, Elliptic Curves, and Hyperbolic Geometry previously seemed like something I might never understand them in this lifetime.

And at the center of it all, I kept finding the same object. Again and again.

---

## The Upper Half-Plane: One Space, Three Approaches

ℍ, the upper half-plane:

$$a + bi$$

where

$$b > 0$$

. Positive imaginary part.

I started with Silverman’s Rational Points on Elliptic Curves, because that’s where FLT proof by Wiles had pointed initially. Elliptic curves over ℂ are tori - quotients of the complex plane by lattices. At first this felt like a technical detail. Then I realized that every lattice is encoded by a single complex number with positive imaginary part. In other words, by a point in the upper half-plane. This was an algebraic number theory perspective on ℍ.

That was in my subconscious when I concurrently started reading about Modular Forms. One can find upper half-plane in chapter 1 itself. A Complex analysis perspective on ℍ.

Again when I picked up Ratcliffe’s Foundations of Hyperbolic Manifolds and there it was again. The same upper half-plane but a geometric interpretation of it.

That’s structure. The unifying object. The same space, appearing in three different contexts.

---

## The Group: SL₂(ℤ)

Why does ℍ appear everywhere? The answer lies in a group: $\text{SL}_2(\mathbb{Z})$, the group of 2×2 integer matrices with determinant 1.

$$\text{SL}_2(\mathbb{Z}) = \left\{ \begin{pmatrix} a & b \\ c & d \end{pmatrix} : a,b,c,d \in \mathbb{Z}, \quad ad - bc = 1 \right\}$$

This group acts on ℍ by Möbius transformations:

$$\tau \mapsto \frac{a\tau + b}{c\tau + d}$$

You can verify this maps ℍ to itself: if τ has positive imaginary part, so does $\frac{a\tau + b}{c\tau + d}$ (the determinant condition $ad - bc = 1$ is what guarantees this).

**For elliptic curves:** An elliptic curve over ℂ is ℂ/Λ for a lattice Λ. We can always write Λ = ℤω₁ + ℤω₂ and, after scaling, normalize to Λ = ℤ + ℤτ where τ ∈ ℍ. But the same lattice has many bases — if we pick a different basis, we get a different τ. The matrix $\begin{pmatrix} a & b \\ c & d \end{pmatrix}$ changes basis: it sends (1, τ) to (c + dτ, a + bτ), which after renormalizing gives τ' = $\frac{a\tau + b}{c\tau + d}$. Same lattice, different τ. So two points in ℍ represent isomorphic elliptic curves if and only if they're related by SL₂(ℤ).

**For modular forms:** Since elliptic curves are really parameterized by ℍ/SL₂(ℤ), functions that depend only on the isomorphism class of the curve must be invariant (or transform predictably) under SL₂(ℤ). A modular form of weight k transforms as:

$$f\left(\frac{a\tau + b}{c\tau + d}\right) = (c\tau + d)^k f(\tau)$$

The factor $(c\tau + d)^k$ appears because we're really tracking how differentials transform, not just functions. Weight-0 modular functions (like the j-invariant) are genuinely invariant.

**For hyperbolic geometry:** The hyperbolic metric on ℍ is $ds^2 = \frac{dx^2 + dy^2}{y^2}$. A direct calculation shows that Möbius transformations from SL₂(ℝ) preserve this metric — they're isometries. The discrete subgroup SL₂(ℤ) acts by isometries with a fundamental domain of finite hyperbolic area. This is why the quotient ℍ/SL₂(ℤ) is a hyperbolic surface (an orbifold, technically, due to fixed points).

![Fundamental Domain](../../../assets/images/FLT-lead-me-to-upper-planes/ModularGroup-FundamentalDomain.svg)

---

## The j-invariant

There's a single function $j: \mathbb{H} \to \mathbb{C}$ that completely classifies elliptic curves over ℂ.

Two elliptic curves are isomorphic if and only if they have the same j-invariant.

The j-invariant is a modular function — it's invariant under SL₂(ℤ), meaning $j(\gamma \tau) = j(\tau)$ for any $\gamma \in \text{SL}_2(\mathbb{Z})$. So it descends to a function on the quotient ℍ/SL₂(ℤ), the moduli space of elliptic curves.

What's remarkable is that j is a *bijection* from ℍ/SL₂(ℤ) to ℂ. Every complex number is the j-invariant of some elliptic curve. The complex plane itself is secretly a moduli space.

And the Fourier expansion of j:

$$j(\tau) = \frac{1}{q} + 744 + 196884q + 21493760q^2 + \cdots$$

where $q = e^{2\pi i \tau}$.

In 1978, John McKay noticed something strange: 196884 = 196883 + 1, where 196883 is the dimension of the smallest non-trivial representation of the Monster group (the largest sporadic simple group). The next coefficient decomposes similarly: 21493760 = 21296876 + 196883 + 1, matching other Monster representation dimensions.

Conway and Norton conjectured this pattern was real — that the coefficients of j are sums of dimensions of Monster representations. Borcherds proved it later.

A function that classifies elliptic curves somehow "knows" about the Monster group.

---

## Three Views of One Structure

Let me now sketch the full picture of how these three areas connect through ℍ.

**Complex Analysis (Modular Forms)**

Modular forms are holomorphic functions on ℍ with that transformation property under SL₂(ℤ). They form finite-dimensional vector spaces for each weight $k$, and their Fourier coefficients encode arithmetic data. The space of weight-12 modular forms for SL₂(ℤ) is one-dimensional, spanned by the Ramanujan Δ function — whose coefficients are Ramanujan's τ function, deep in the theory of partitions and L-functions.

**Algebraic Number Theory (Elliptic Curves)**

An elliptic curve over ℂ is ℂ/Λ for a lattice Λ. Up to scaling, Λ is determined by τ ∈ ℍ. But the arithmetic gets serious when we look at elliptic curves over ℚ. The Modularity Theorem says every elliptic curve over ℚ corresponds to a weight-2 modular form. This is what Wiles proved (for semistable curves) and what implies FLT.

**Geometry (Hyperbolic Manifolds)**

Equip ℍ with the metric $ds^2 = \frac{dx^2 + dy^2}{y^2}$, and it becomes the hyperbolic plane — constant curvature −1. The group SL₂(ℝ) acts by isometries; SL₂(ℤ) is a discrete subgroup. Hyperbolic manifolds arise as quotients by such discrete groups, and their geometry encodes number-theoretic information (volumes relate to special values of zeta functions, for instance).

---

## Another Coordinate System: The p-adics

But ℍ isn't the only fundamental space. There's another coordinate system that keeps appearing: the p-adic numbers.

For each prime p, there's a different way to measure "closeness" of integers. In the usual (Archimedean) sense, 1000000 is far from 0. But in the 5-adic sense, $5^{10}$ is *extremely* close to 0 — because it's divisible by a high power of 5.

This gives you $\mathbb{Q}_p$, the p-adic numbers: a completion of the rationals that's entirely different from ℝ. And $\mathbb{Q}_p$ has its own geometry, its own analysis, its own version of "the upper half-plane" (the p-adic upper half-plane, due to Drinfeld).

Here's what's wild: the full picture of an elliptic curve, or a modular form, or a Galois representation, requires looking at it from *all* these perspectives simultaneously. The real place (classical complex analysis on ℍ) and all the p-adic places. The mathematical object exists in some higher-dimensional sense, and each prime gives you a different projection.

This is where deep theorems live — they tell you how to reconstruct information at one place from information at others.

---

## A Teenager, a Theorem, and a New Geometry

I'm not the first person to fall into deep mathematics through FLT. Peter Scholze got interested in advance math because he wanted to understand Andrew Wiles' proof. Scholze, Fields Medalist is known for his work in arithmetic geometry.

But something has changed for me. A year ago, if you'd shown me a paper mentioning perfectoid spaces or p-adic Hodge theory, I would have understood nothing — not even the shape of what I didn't understand. Now I can read the introductions. I can follow the motivation. I can see *why* these ideas exist, even if I can't produce them myself.

I am not a mathematician but probably I will be a "mathematically-literate person".

---

## The Langlands Program

The Langlands Program is a set of conjectures about connections between number theory, algebra and geometry.

The Modularity Theorem - the heart of Wiles' FLT proof — is a *special case* of Langlands.

But Langlands goes further. It predicts correspondences for much more general groups, in much more general settings. It ties together representation theory, algebraic geometry, number theory, and harmonic analysis into a single (still incomplete) vision.

Langlands Program is often referred to as a "grand unified theory".

---

## Conclusion: A New Mathematical Landscape

I set out to understand a single theorem's proof. I ended up getting slowly confident to dive deep into advanced mathematics.

The experience has changed how I think about mathematics. I used to see it as a collection of isolated fields — analysis, number theory, algebra, topology, etc. However, I was able to build an intuition about the deep structures that connect these fields. The intutitions are still fuzzy and brittle but they are there.

I don't fully understand that unity. I'm still in the early chapters of three different textbooks. I can't prove the theorems or solve problems on my own yet. It will take me some time to get there.

I am happy that there is a possibility that in this lifetime, I will understand the work of thinkers like Terence Tao, Maryam Mirzakhani and other great mathematicians.

---

**What I'm Reading**

- *A First Course in Modular Forms* (Diamond & Shurman) — GTM 228
- *Foundations of Hyperbolic Manifolds* (Ratcliffe) — GTM 149  
- *Rational Points on Elliptic Curves* (Silverman & Tate)

**Previous Post**

- [I Tried to Understand Fermat's Last Theorem](https://vaibhawvipul.github.io/2025/11/25/I-tried-to-understand-FLT.html)
- [Beauty as Residue](https://vaibhawvipul.github.io/2025/11/04/Beauty-as-residue.html)
