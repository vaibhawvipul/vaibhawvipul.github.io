---
layout: post
title: 'How to Hire Engineers Who Ship Kernels'
date: 2025-04-22
author: "Vipul Vaibhaw"
---

**
Note - This is from my perspective and learnings as a founding engineer. This is my personal take on how to build tech teams for the future. Not affiliated with any company or my current employer.

Also, this is just a quick note rather than a well thought article. I will be expanding on this in the future.
**

> History shows that real leverage comes from those who build the foundations.

Most hiring processes today optimize: glue work. Flashy resumes. Fancy titles. Shallow experience wrapped in buzzwords.

But here’s the truth: glue engineers won’t build your company's deep tech foundation. You need to be clear about what you’re looking for. Innovators or assemblers?

Assemblers: They’ll take your existing components and slap them together. They’ll use libraries they usually don’t understand. They’ll follow the latest trends without questioning them. They’ll be great at using tools, but they won’t know how to build them.

Mostly this is a recipe for mediocrity. An illusion of progress and a trap of massive tech debt.

Early-stage deep-tech startups don’t need assemblers. They need real builders.

Deepseek is a great example of what kernel-grade engineers can do. [They built several systems from scratch, including a new distributed file system, efficient parallel expert communication library etc](https://github.com/deepseek-ai).

## The Problem with Glue Engineers

Glue engineers know the tools. They know the frameworks. They know which package to install. But ask them to build the tool itself — the database, the compiler, the scheduler — and they’re lost.

They won’t build the next kernel.
They won’t write the next compiler.
They won’t create the next database.
They won’t design the next OS.
They won’t invent the next hypervisor.
They won’t architect the next distributed system.

They’re great at using the tools.
But they’re not the ones who will build them.

Glue Engineers usually work at an abtraction where they don’t have to think about the underlying systems.

They can’t debug a kernel panic. They can’t write a compiler from scratch. They can’t design a new protocol.

## What Makes a Kernel-Grade Engineer?

Forget CVs or LeetCode. They’re not the best signals of high-leverage engineers. They can be faked.

Look for these signals instead:

1. **A Bias for Building, Not Assembling**
High-leverage engineers don’t just know how to use tools. They know how to build them.

2. **First-Principles Thinking**
They aren’t bound by “the way things are done.” They can derive solutions from scratch if needed.
-> Jim Keller once sketched a CPU pipeline on a napkin that outperformed teams of engineers.

3. **Small Systems, Deep Understanding**
Their early projects aren’t trendy, but they’re complete: a bootloader, a compiler, a DSL, a VM, a new build system.
-> Hotz’s Tinygrad: 1,000 lines of code, can train transformers. Not because it’s practical — because it’s possible.

4. **Love of Craft, Not Just Scale**
They optimize for correctness, simplicity, and beauty — even in obscure corners.
-> Aaron Swartz dove into RFCs and protocol specs, not for school, but for fun.

5. **Restless Curiosity**
They don’t just build what they know. They build to learn what they don’t.
-> Turing wasn’t “qualified” to break the Enigma machine. He just did it anyway.

## How to Find Them

These people are rare. They aren’t always easy to work with. They will call out bullshit when they see it.

Look at their side projects. Are they the kind of person who wrote their own debugger, hypervisor, or kernel scheduler… just because?
Ask about a system they deeply admire. Can they explain why it’s beautiful? Can they break it down and rebuild it in words?

Give open-ended design prompts. “Sketch a compiler pipeline.” “Design a reliable message bus.” Watch for joy and rigor.

## The Payoff

Most engineers can glue. Few can forge. But the ones who can — they create leverage that compounds.

If you’re lucky enough to find one: Don’t waste them on CRUD.

when you find one: Don’t give them your Jira board. Give them your hardest problem. Get out of their way. Let them build.
