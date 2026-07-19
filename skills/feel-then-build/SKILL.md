---
name: feel-then-build
description: Use when the user wants to scope a brand-new feature or product and wants to stay in control of both the experience and the implementation before any code is written, or invokes /feel-then-build.
disable-model-invocation: true
---

# Feel Then Build

A relentless, two-part interview for scoping a new feature while the user keeps every
decision. You write no files and no code. The output is the conversation itself: a shared
understanding the user can hand to any structuring method (SDD/Spec Kit, a PRD, a ticket).

## Core rules (both parts)

- Ask exactly one question at a time. Wait for the answer before the next. Multiple
  questions at once is bewildering.
- For every question, give your recommended answer with a one-line why — but the decision
  is the user's.
- Walk the decision tree by dependency: resolve what unblocks other choices first.
- If something is a *fact* you can look up (files, tools, docs), look it up. Only
  *decisions* go to the user.
- Never jump to implementation, code, or file writes until told. This skill produces
  understanding, not artifacts.

## Part 1 — The Feel (experience only)

Interrogate how the user should *feel* using this, and what it does — never how it's built.
Cover: who it's for, the core job, the emotional/UX target (fast? calm? powerful?
guided?), the key moments and flows, what's in scope vs deliberately out, what "good"
feels like. Abstract each idea into a named functionality. Keep pulling until the set of
functionalities and the intended experience are sharp and the user confirms nothing is
missing. No stack, no routes, no data model here.

### Checkpoint

Play back the full list of functionalities from Part 1 in the user's words. Do not enter
Part 2 until the user confirms the list is complete and correct. This is their gate.

## Part 2 — The Build (one functionality at a time)

Take the confirmed list. Grill implementation for ONE functionality at a time, fully,
before moving to the next. Per functionality, put decisions to the user — recommend, but
they choose: the **product logic** (how it actually behaves, edge cases, states, rules)
first and most thoroughly, then stack, routes/endpoints, data shape, and dependencies.

After locking each functionality, stop and reason out loud: does anything just decided
create a downstream adjustment, a new open question, or force revisiting a functionality
already closed? If so, name it and fold it back into the queue before continuing. Nothing
is "done" if a later decision can still reshape it.

## Ending

When every functionality's experience and implementation are locked and
dependency-checked, synthesize the whole thing in-chat: the functionalities, the
experience they deliver, and the locked implementation decisions per functionality.
Present it as reusable context the user can drop into SDD/Spec Kit or any structuring
method. Do not write files. Do not start building until the user says so.
