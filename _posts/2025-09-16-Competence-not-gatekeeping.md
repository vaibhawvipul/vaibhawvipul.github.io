---
layout: post
title: 'The Systems Programmer Extinction Event'
date: 2025-09-16
author: "Vipul Vaibhaw"
---

We're living through a mass extinction event in software engineering. Competence is eroding with vibes!

I recently asked a recent grad to explain "Who is responsible for terminating a process in assembly - the program, the runtime, or the OS - and what happens if no exit path is taken?" They had no clue. Btw, this is a question every CS grad should be able to answer. The answer is segfault(most commonly). Ideally a program Should request termination via exit syscall.

People have pounced upon this ignorance to push the narrative that "knowing how computers work isn't important anymore."

These aren't trivia questions—this is the foundation their entire career is built on.

I recently read Dr. Barbara Liskov, Turing Award winner, say:
![Barbara Liskov Tweet](../../../assets/images/The-Systems-Programmer-Extinction-Event/Screenshot 2025-09-16 at 12.38.31 PM.png)
reference - [ACM Turing Award Interview](https://amturing.acm.org/pdf/LiskovTuringTranscript.pdf)

## The Competence Crisis

This isn't gatekeeping. This is about competence.

- Performance Engineering is a lost art.
- Very few people use debuggers anymore.
- Profiling is a black box.
- Few understand memory management beyond "there's a garbage collector."
- "Semaphores vs Mutexes" is a mystery.

We don't want a generation of operators. We need a generation of builders - Once the AI hype dies down, the real work of building better programming languages, runtimes, and systems will begin. It is again, not sexy, but it is necessary.

We have CS graduates who can leetcode but can't tell you how a CPU works. An entire generation that thinks the computer is a browser.

## The Hard Truth

Yes, you can have a successful career without understanding pointers. Yes, many products succeed despite inefficiency. Yes, abstractions enable developers to build amazing things without deep knowledge.
But this is a house of cards. The abstractions will fail. The systems will break. The performance bottlenecks will appear. And when they do, who will fix them?

See the problem is not about "systems programming" specifically. The problem is about cultivating deep technical competence and systems thinking!

You want to be valuable in 10 years?
- Learn what nobody else wants to learn.
- Understand the machine.
- Read the manuals.
- Write a kernel module.
- Implement malloc().

The extinction event isn't coming. It's here. And we're too busy debating tabs vs spaces to notice.

Note - I am not against abstractions or high-level programming. I am against ignorance and complacency. Please do not confuse the two. One can be a high-level programmer and still understand the underlying systems.

---

These are my reflections. Please feel free to completely disagree and do share your thoughts.

reach out on [x](https://x.com/vaibhaw_vipul) or [github](https://github.com/vaibhawvipul) or [email](vaibhaw.vipul@gmail.com) for more.
