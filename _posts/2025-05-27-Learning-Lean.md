---
layout: post
title: 'Why I’m Learning Lean: A Systems Engineer’s Mathematical Adventure'
date: 2025-05-27
author: "Vipul Vaibhaw"
---

As a systems engineer with a math background, I've always been fascinated by the intersection of logic and computation. Recently, I started learning Lean, a theorem prover that lets you write mathematical proofs the computer can verify. It's surprisingly fun - there's something deeply satisfying about proving that `odd × odd = odd` and watching Lean confirm your reasoning is airtight.

```
theorem odd_mul_odd {m n : ℕ} (hm : Odd m) (hn : Odd n) : Odd (m * n) := by
  match hm, hn with
  | ⟨j, hj⟩, ⟨k, hk⟩ =>
    -- We claim that 2*j*k + j + k is the value that makes m*n = 2*(2*j*k + j + k) + 1
    exists 2 * j * k + j + k

    calc
      m * n = (2 * j + 1) * (2 * k + 1) := by rw [hj, hk]
      _     = 4 * j * k + 2 * j + 2 * k + 1 := by ring
      _     = 2 * (2 * j * k + j + k) + 1 := by ring
```

**Why This Matters**

Beyond the immediate joy of puzzle-solving, Lean is teaching me to think.

Every step must be justified, every assumption explicit. This mindset translates beautifully to systems engineering, where unclear specs maybe costly.

**Long-term Benefits I'm Excited About:**

- **Better code quality**: Formal verification techniques are entering mainstream software development
- **Enhanced problem-solving**: Mathematical reasoning sharpens analytical thinking for complex system design
- **Future-proofing career**: As AI assists more coding tasks, human expertise in formal methods becomes increasingly valuable
- **Cross-domain skills**: Lean bridges pure mathematics and practical programming

**My Learning Plan**

For the next month, I'm committing to writing at least one proof every couple of days while working through two excellent resources: [Mathematics in Lean](https://leanprover-community.github.io/mathematics_in_lean/C01_Introduction.html) and [Theorem Proving in Lean 4](https://leanprover.github.io/theorem_proving_in_lean4/title_page.html). This consistent practice should build the muscle memory needed for formal reasoning.

It's early days, but I'm convinced this mathematical playground will make me a better engineer.
