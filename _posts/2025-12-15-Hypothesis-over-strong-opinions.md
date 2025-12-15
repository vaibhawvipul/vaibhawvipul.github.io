---
layout: post
title: "The 'Strong Opinion' Fallacy: Why I Prefer Strong Hypotheses in startups"
date: 2025-12-15
author: "Vipul Vaibhaw"
---

*Not affiliated with any company or my current employer.*

In Tech especially startups, **“Strong Opinions, Loosely Held”** has taken over the narrative. The mantra is meant to prevent analysis paralysis.

The approach is simple: take a position with full conviction to get the team moving, then pivot instantly when new data arrives.
Theoretically it sounds nice, but I have seen it making organizations unworkable and toxic. It has a fundamental flaw. It assumes humans to be **stateless**!

Humans are not stateless - that we can emit a *Strong Opinion* at *t = 0* and cleanly overwrite it at *t = 1* with no residual state.

I am not a biologist or psychologist but I think that is not how it works!

---

## The Biological Debt of Certainty

Humans are stateful complex neurological systems. The more states we get into, it results in more ego, fatigue and trust-erosion.

When we publicly articulate a position with high certainty, something subtle happens. The opinion stops being a hypothesis and starts becoming an identity. *Identity-protective cognition*. When that belief/opinion is challenged, it often feels like a personal attack.

I’ve watched this play out in real systems/orgs. Loudest voice often win, egoistic-uncouth people often win here.

Often, a confident-sounding architectural call is made. Code gets shipped on an arbitary deadline(which was also set on the basis of a strong opinion). People get hired(on strong opinion). Weeks later, the data starts to disagree.

At that point, even if the original decision-maker intellectually wants to pivot, the system resists. Nobody wants to be the person who admits the expensive thing they just built was wrong. If they do agree, that is they fire the person they hired or re-think the feature they shipped, it creates a damage to the org which is often irrecoverable.

By starting with a *Strong Opinion*, we preload the system with confirmation bias. Dissent feels costly. The opinion isn’t being held loosely — **the opinion is holding you**.

This is biological debt. And like technical debt, it compounds quietly.

---

## The Motte-and-Bailey Failure Mode

In teams, this mantra often degrades into a rhetorical exploit known as the *Motte-and-Bailey fallacy*.

Leaders bulldoze nuance with performative certainty. Believe you me(or Trust me bro) - If you challenge them, they retreat to the convinient-defensible position:

> “Oh, I was just holding it loosely.”

But until you produce overwhelming evidence, they govern as if they have divine revelation.

This dynamic destroys signal-to-noise. It promotes eccentricity. Performance over truth. Singalling over thinking.

If a Principal Engineer states something with absolute conviction, a Junior Engineer needs an order of magnitude more courage to raise a legitimate edge case. The social cost of dissent becomes higher than the technical cost of being wrong.

That’s not velocity. That is a way to silent-death of a startup.

---

## Orgs have inertia: Cost of moving fast mindlessly

> “We need to move fast.”

Moving at an incredibly fast speed with false inertia is stupid. I hope that is self-explanatory. This is a common outcome of "Strong Opinions held loosely".

It is almost always cheaper to spend an extra day forming a correct hypothesis than to spend three months unwinding a confident but wrong decision. This is because organizations have an inertia, moving fast in wrong direction creates debts faster!

---

## The Patch: Falsifiable Hypotheses

I fail to realize, in tech, why do we need opinions at all? We need a **scientific method**.

I prefer replacing the mantra with:

> **Strong hypotheses, held tentatively.**

The difference between an opinion and a hypothesis is **falsifiability**. For a theory to be scientific, there must be a specific test that could prove it false. If you cannot define a scenario where you are wrong, you aren't doing science. You are doing theology.

**Opinion**
> “Rust is the best language for this service.”
*(A statement of belief. Invites alignment and sounds authoritative.)*

**Hypothesis**
> “If we build this service in Rust, we expect a 40% reduction in tail latency. We will know we are wrong if compile times slow deploys by more than 20%.”
*(A statement of logic. Invites debate and discussion. Easy to argue against scientifically as well)*

Most importantly, a hypothesis decouples ego from the variable.
You’re not disproving *me* - you’re disproving an assumption.

---

## Probabilistic Leadership

In practice, this means encouraging probabilistic thinking.

Instead of saying:

> “This is the way.”

We prefer:

> “I’m about 70% confident this is the right path. However, here’s the 30% failure mode that worries me.”

Two things happen immediately:

1. **You invite collaboration.** The team is explicitly asked to help patch the failure mode.
2. **You lower the cost of being wrong.** Updating beliefs becomes an expected outcome, not a loss of face.
3. **You increase trust and equality in the system** - Hypothesis allow meritocracy to flourish and forces everyone to generate more signal as compared to noise. Also, a vulnerable leader is more trust-worthy as compared to an arrogant person who has 100% conviction but 50% success rate.

---

## Conclusion

Certainty is not a badge of leadership. Often, it’s just a mask for insecurity.
I often believe that maturity in life or as a leader refers to handling uncertainity with transparency.

We engineers live in a world of trade-offs, invariants, edge cases, and failure modes. Our communication should reflect that reality — not hide it behind slogans that reward charisma over correctness.

Strong hypotheses allow startups to be more resillient. Strong opinions are fragile. Strong hypotheses are anti-fragile as they have to backed by evidence and science.

---

reach out on [x](https://x.com/vaibhaw_vipul) or [github](https://github.com/vaibhawvipul) or [email](vaibhaw.vipul@gmail.com) for more.
