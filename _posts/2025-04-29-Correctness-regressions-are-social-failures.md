---
layout: post
title: 'Correctness Regressions Are Social Failures'
date: 2025-04-29
author: "Vipul Vaibhaw"
---

**
Note - These are reflections from my experience building and scaling technical systems as a founding engineer. I intend to expand this further.
**

## Correctness Regressions Are Social Failures

Correctness regression - A correctness regression occurs when a system that once behaved correctly starts behaving incorrectly, violating previously valid assumptions or guarantees.

Correctness regressions are common, especially in large and evolving systems.

A bug is something you never got right.
A correctness regression is something your team once understood — and then forgot.

When systems break, the first explanations are usually technical:
- missing test coverage,
- tech debt,
- legacy complexity,
- race conditions nobody caught.

Technical debt is visible; contract debt is silent — until catastrophe.

We blame flaky infrastructure and brittle dependencies, believing that fixing code alone will stop regressions.

But that's not the real story. It's not even the most important part.

Most correctness regressions aren't technical failures. **They are social failures.**

They happen not because the code was broken, but because the understanding between people was broken:
- A missing conversation.
- An unspoken assumption.
- A silent fear of asking the obvious question.
- A lack of clarity about who owns what.
- A misalignment about what "correct" even means.

The real causes don't show up in Git logs or postmortems.

They live in the culture — in the invisible rituals of how teams talk, listen, and build together.

Before the bug ever reached the codebase, something else had already regressed:
- trust,
- clarity,
- and alignment.

Regressions are the symptoms of a deeper disease: a breakdown in the social contract between people.
The code is a manifestation of that contract, but the real problem is upstream.

## The Hidden Parallel: Correctness as Social Engineering

Correctness regressions behave like social engineering attacks — but the attacker is inside.

In cybersecurity, social engineering doesn't hack computers directly. It hacks people: their assumptions, their blind spots, their trust.

A phishing email doesn’t break encryption. It tricks the human into opening the door. A fake tech support call doesn’t crack the server. It persuades someone to hand over the keys.

Similarly, regressions often bypass all technical defenses — tests, CI pipelines, static analysis - by exploiting the soft tissue of teams:
- An unstated invariant.
- A fragile contract.
- A "common knowledge" spec that no one actually wrote down.

In both cases, the real vulnerability isn’t technical. It’s social.

Nancy Leveson, in Engineering a Safer World, argues that most accidents in complex systems stem not from individual component failures, but from inadequate control and flawed communication across the system. Software correctness is no different.

When communication degrades, correctness follows. And by the time the system fails, the real failure has already happened — silently, invisibly, upstream.

## The Path Forward: Building a Culture of Correctness

If regressions are social failures, fixing them requires more than better tooling.
It demands a cultural and technical shift. Here’s how.

1. Specify Before You Code -
   - Before you write a line of code, write down the assumptions, invariants, and contracts. Make them explicit. This is your social contract. Formal specifications are great, but even informal ones are better than nothing. The key is to make them visible and shared.
2. Exhaustive Review -
   - Review not just the code, but the contracts. Ask questions like:
     - What assumptions are we making?
     - What invariants are we relying on?
     - What happens if those assumptions break?
   - Make it a habit to question the social contract, not just the technical one.
3. Pair Programming and Mob Programming -
   - Encourage pair programming or mob programming sessions. This creates a shared understanding of the code and its contracts. It’s harder to miss something when multiple people are involved.
4. Adversarial Testing -
   - Test not just for the happy path, but for edge cases and failure modes. Think like an attacker. What could go wrong? What assumptions are you making that could be exploited?
5. Run the system in a "sandboxed, deterministic world":
   - Deterministic Simulation Testing to validate correctness across non-deterministic runs.

Culture guards correctness. But culture alone isn't enough — we need technical defenses too. Systems should catch what people inevitably miss.

1. Make Implicit Knowledge Explicit -
   - Push for written specs, design notes, docstrings, diagrams. Writing as a tool for thinking not as a chore or afterthought.
2. Psychological Safety for “Stupid Questions” -
    - Praise identification of unclear contracts or missing invariants during review.

## Conclusion

> Correctness is never automatic.
> It must be guarded — by thought, by trust, and by teams who know why it matters.

Thinking is not the enemy of speed — ignorance is.

Correctness doesn't erode all at once.
It frays slowly — at the edges of conversation, trust, and care.
In the end, systems don't fail because people weren't smart enough.
They fail because teams forgot to guard what they once knew.

Guard your correctness like your future depends on it. Because it does.


## References
- [Engineering a Safer World by Nancy G. Leveson. MIT Press.](https://mitpress.mit.edu/9780262533690/engineering-a-safer-world/)

Drafted with AI assistance for speed; all ideas and judgments are mine.
