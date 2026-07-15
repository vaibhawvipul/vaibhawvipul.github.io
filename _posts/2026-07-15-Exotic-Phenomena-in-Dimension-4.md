---
layout: post
title: "Exotic Phenomena in Dimension 4"
date: 2026-07-15
author: "Vipul Vaibhaw"
tags: [mathematics, topology, four-manifolds, exotic-structures, low-dimensional-topology]
excerpt: "My notes from Lisa Piccirillo's lecture on exotic 4-manifolds — where a space can be homeomorphic but not diffeomorphic, the smooth Poincaré conjecture is still open, and the smallest manifolds turn out to be the hard ones."
---

A lecture by Lisa Piccirillo called *Exotic Phenomena in dimension 4* was on my watch later for so long and YT kept recommending it. This week I made sure I sat through it after office. This post is me going back over the notes I took for myself.

I would like to point out again: I am not a mathematician. I am a math grad who reads this stuff for fun after work. I feel that I can probably follow the *shape* of these ideas. So read this as one enthusiast's reconstruction of a lecture, not as an expert account.

---

The lecture focuses on Dimension 4. The reason being that this is the dimension where smooth and topological structures start to diverge in a strange way. The talk is about the *exotic phenomena in 4D*, where two manifolds can be homeomorphic but not diffeomorphic.

![Lisa Piccirillo lecturing on exotic phenomena in dimension 4](../../../assets/images/Exotic-Phenomena-in-Dimension-4/piccirillo-exotic-4-manifolds-lecture.png)

*Source: [Lisa Piccirillo, "Exotic Phenomena in dimension 4", Harvard Mathematics Department](https://www.youtube.com/watch?v=BXwALAkPubc).*

---

## The setup

The goal of the subject is to classify manifolds. A manifold is a space that locally looks like flat $$n$$-dimensional space. Piccirillo fixes the conventions early: everything is oriented, compact, with no boundary.

There are (at least) three categories:

- **Topological manifolds** — no extra structure. Two manifolds are the same if they are *homeomorphic*: there is a continuous map with continuous inverse.
- **Smooth manifolds** — the manifold carries a $$C^\infty$$ structure, and "the same" means *diffeomorphic*: the map and its inverse are smooth.
- **PL** — not covered in the talk, because in dimension 4, PL and smooth coincide.

Diffeomorphic is strictly stronger than homeomorphic.

## How the dimensions split

- In dimensions 1, 2, 3: smooth $$=$$ topological. Every topological manifold has exactly one smooth structure.

- In high dimensions ($$\geq 5$$): smooth $$\neq$$ topological, but *surgery theory* reduces the classification of manifolds to problems in algebraic topology. So the situation is under control.

- In dimension 4: smooth $$\neq$$ topological, and neither the low-dimensional hands-on methods nor surgery theory fully work. This dimension needs tools of its own, and it behaves strangely.

## Fundamental group and intersection form

For this lecture, the fundamental group $$\pi_1$$ is the primary invariant of a manifold. It measures the loops in the space up to continuous deformation. The second invariant is the **intersection form**. It is a symmetric bilinear form on $$H_2$$. Two surfaces inside a 4-manifold generically meet in isolated points, and if you count those points with signs you get an integer. Doing this across a basis of $$H_2$$ gives a symmetric unimodular form $$Q\colon \mathbb{Z}^n \times \mathbb{Z}^n \to \mathbb{Z}$$.

## The topological category in dimension 4

Surgery theory does work *topologically* in dimension 4 when the fundamental group is "good," and the cleanest good group is the trivial one. So restrict to simply-connected manifolds ($$\pi_1 = 1$$).

Freedman's theorem (1982) is then a bijection, up to a caveat I've parked in a footnote:

$$\{X^4 \text{ topological, } \pi_1 = 1\} \longleftrightarrow \{Q\colon \mathbb{Z}^n \times \mathbb{Z}^n \to \mathbb{Z} \text{ unimodular, symmetric}\}$$

Hand over the algebra and you get back the manifold. So topologically, the simply-connected case in dimension 4 is a solved problem.

## Exotic manifolds

Now the smooth side. A smooth 4-manifold $$X$$ is **exotic** if there is another manifold $$X'$$ that is homeomorphic to $$X$$ but not diffeomorphic to it. It is the same topological space, but it carries two smooth structures and no smooth map connects them.

Two facts frame the talk:

1. The **smooth 4-dimensional Poincaré conjecture** says that $$S^4$$ is not exotic. That is, every smooth manifold homeomorphic to the 4-sphere should be diffeomorphic to it. This is wide open.
2. Exotic 4-manifolds *do* exist, in abundance. We just cannot decide the most famous case.

For contrast, dimension 4 even has smooth manifolds that are homeomorphic but not diffeomorphic to $$\mathbb{R}^4$$, and in fact uncountably many of them. It is the only dimension where Euclidean space has more than one smooth structure.

The main question of the talk:

> **Which small smooth 4-manifolds are exotic?**

where "small" means the fundamental group is trivial ($$\pi_1 = 1$$) and the second Betti number $$b_2$$ is small. The basic small manifolds are $$S^4$$, $$\mathbb{CP}^2$$, $$\overline{\mathbb{CP}}^2$$, and connected sums like $$\mathbb{CP}^2 \# \overline{\mathbb{CP}}^2$$. This is a strange inversion. In dimension 4, it is the *small* manifolds that are the mysterious ones. From here on, all manifolds are smooth and simply connected.

## How to build exotic manifolds

The recipe has three steps:

1. **Build a pair** of smooth manifolds $$X$$ and $$X'$$ which you reasonably think might be homeomorphic but not diffeomorphic.
2. **Show they are homeomorphic**, $$X \cong_{\text{Top}} X'$$. Compute $$\pi_1$$ and the intersection form; if they match, Freedman gives the homeomorphism. This step is solved.
3. **Show $$X \not\cong_{\text{Sm}} X'$$.** This is where all the difficulty is.

Where do candidate pairs come from? Piccirillo's list of constructions:

- Products and bundles
- Complex surfaces and symplectic manifolds ("ask a geometer"), which have supplied many of the examples
- Cut-and-paste operations
- Handles

## Distinguishing manifolds, and where the tools fail

Step 3 needs invariants that can see smooth structure. The main tool here is **gauge theory**: Donaldson's invariants, and later the Seiberg–Witten invariants. They count solutions to certain PDEs on the manifold, and the numbers that come out do not change under a homeomorphism.

Piccirillo was upfront about two limitations:

- There is often **no explicit computation**. There is no formula you can just plug into.
- The invariants are **no good when $$b_2 = 0$$**.

The second limitation is the real problem. $$b_2 = 0$$ is exactly the small case where $$S^4$$ lives. So the strongest tools we have say nothing about the one question we most want to answer.

## Casson's approach

So people look for step-3 arguments that avoid gauge theory. Casson's approach turns the problem into knot theory.

Let $$X \cong_{\text{Top}} X'$$. Suppose you can find a knot $$K \subset S^3$$ such that:

1. $$\exists\, D^2 \subset_{\text{Sm}} X$$ with $$\partial D = K$$ — the knot bounds a smoothly embedded disk in $$X$$;
2. $$\nexists\, D^2 \subset X'$$ with $$\partial D = K$$ — no such disk exists in $$X'$$.

That implies $$X$$ and $$X'$$ are not diffeomorphic, since a diffeomorphism would carry the disk in $$X$$ over to a disk in $$X'$$. The 4-manifold question turns into a *sliceness* question about a knot, which is something knot theorists have tools for.

**Pros:** the approach is strong enough to show that $$\mathbb{R}^4$$ is exotic. The non-compact version of the smooth Poincaré conjecture is false.

**Cons:** in practice, it is very hard to find the knot.

## Manolescu–Piccirillo

Some background: Piccirillo is the topologist who in 2020 settled whether the Conway knot is slice (it is not), so knot sliceness is her home turf, and turning 4-manifold questions into knot questions is a natural move for her.

With Ciprian Manolescu, she gave a systematic method for producing manifolds $$X \cong_{\text{Top}} S^4$$ that come with a knot $$K$$ as in condition (1) above. The construction is rigged so that $$K$$ is slice in $$X$$ exactly when $$X$$ is the standard sphere. You then feed $$K$$ into a *computable* invariant like Rasmussen's $$s$$-invariant, which comes from Khovanov homology. If it comes back nonzero, you have found an exotic $$S^4$$ and disproved the smooth Poincaré conjecture.

They produced concrete families of examples and computed the invariants on them. So far there is no counterexample; the invariants have not obstructed sliceness on any candidate yet. One thing she mentioned stuck with me. A few people are now using machine learning to run this construction and check the candidates, training neural networks to search the huge space of knots for one that finally trips the invariant.

## Where does exotica come from?

Let $$X \cong_{\text{Top}} X'$$. An observation: if $$X$$ and $$X'$$ cobound a 5-manifold $$W$$ that is a product, $$W \cong X \times I$$, then $$X \cong_{\text{Sm}} X'$$.

Wall proved in 1964 that homeomorphic simply-connected 4-manifolds always cobound an **h-cobordism** $$W$$. This is a 5-manifold with $$X$$ and $$X'$$ as its two ends, where each end is a deformation retract of the whole thing. In dimensions $$\geq 5$$, Smale's h-cobordism theorem says such a $$W$$ is always a product, so there is no room for exotica. In dimension 4, the h-cobordism theorem holds topologically (Freedman again) but *fails smoothly*. The cobordism exists but need not be a product, and the exotic difference between $$X$$ and $$X'$$ lives in that failure.

The **cork theorem** makes this sharper. Any two homeomorphic simply-connected smooth 4-manifolds differ by a single cork twist. You cut out one compact contractible piece and glue it back by an involution of its boundary. All the exotic difference between them sits inside that one piece. And the piece is contractible, so to topology it is almost invisible.

## Handles

Underneath the constructions is one fact from Morse theory ("Morse '32" was on the board): **all smooth manifolds can be built from handles**. You start with a ball and attach thickened cells one at a time: 1-handles, 2-handles, and so on.

Here is why this matters. In dimension 4, a 2-handle is attached along a *knot* in the boundary, together with a framing. So building a 4-manifold is, at bottom, an exercise in knot theory. That is why knots keep showing up everywhere: in Casson's approach, in the Manolescu–Piccirillo construction, all through the subject.

---

**Footnotes**

[1] The lecture: [Lisa Piccirillo, *Exotic Phenomena in dimension 4*, Harvard Mathematics Department](https://www.youtube.com/watch?v=BXwALAkPubc). All the notes here are my reconstruction of it; any errors are mine, not hers.

[2] Freedman's classification has a small correction I glossed over: for each unimodular form there are one or two topological manifolds, told apart by the $$\mathbb{Z}/2$$-valued Kirby–Siebenmann invariant. The clean "forms ↔ manifolds" bijection is the right thing to remember first.

[3] Piccirillo, *The Conway knot is not slice*, Annals of Mathematics (2020). Manolescu–Piccirillo produced potential counterexamples to the smooth 4-dimensional Poincaré conjecture using knot invariants (2021).

---

Earlier posts from the same side-quest: [The Shared State of Mathematics](https://vaibhawvipul.github.io/2025/12/30/FLT-helped-me-find-upper-planes.html) and [Hyperbolic Geometry, Part 1](https://vaibhawvipul.github.io/2026/05/07/Hyperbolic-Geometry-part-1.html).

reach out on [x](https://x.com/vaibhaw_vipul) or [github](https://github.com/vaibhawvipul) for more.
