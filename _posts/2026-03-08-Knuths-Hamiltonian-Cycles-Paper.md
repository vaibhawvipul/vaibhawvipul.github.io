---
layout: post
title: "Notes on Knuth's Hamiltonian Cycles Paper"
date: 2026-03-08
author: "Vipul Vaibhaw"
---

I read Knuth's paper in detail. Following is what I understood.

A Hamiltonian cycle visits every vertex in a graph exactly once and returns to the start.

In this paper the graph is 3-dimensional.

Imagine a 3D grid of points - every combination of (i, j, k) where each coordinate runs from 0 to m-1. For m=3, that's 27 points. For m=5, that's 125.

From every vertex, exactly three directed edges leave. And the grid wraps around: increment past m-1 and you're back at 0. So it's not a cube - it's a 3D torus.

This gives us 3m^3 directed edges in total.

The problem statement is - Can we partition all 3m^3 edges into exactly 3 groups, such that each group forms one single Hamiltonian cycle?

**Why is this hard?**
- There are (3!)^(m^3) possible assignments
- Validity check is inherently global

Knuth had already solved m=3 by hand. A friend verified solutions empirically for m up to 16. So the solutions exist, but they are searching for a generalized answer.

---

**What's genuinely impressive -**

Claude reframed the problem (Cayley digraph -> fiber decomposition -> coordinate-local rules), each reframing being mathematically non-trivial.

**What to not miss -**

- Filip had to repeatedly remind Claude to document progress, restart sessions when it crashed on errors, and lost search state multiple times. 31 explorations with manual supervision is not autonomous research — it's a very fast, creative collaborator that needs hand-holding.
- Claude found empirical solutions for m=4,6,8 but couldn't generalize them and eventually "stopped writing correct programs." Claude can do good directed search + pattern matching. Not yet build new abstractions.
- Filip gave Claude the exact problem statement, a structured workflow, and empirical data up to m=16. This isn't cold-start mathematical discovery.

Paper: [claude-cycles.pdf](https://cs.stanford.edu/~knuth/papers/claude-cycles.pdf)

---

*I love math and systems engineering.*
