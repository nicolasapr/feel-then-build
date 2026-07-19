---
name: feel-then-build
description: Use when the user wants to scope a brand-new feature or product and wants to stay in control of both the experience and the implementation before any code is written, or invokes /feel-then-build.
disable-model-invocation: true
---

# Feel Then Build

A relentless, two-part interview for scoping a new feature while the user keeps every
decision. You write no files and no code — the output is a shared understanding the user
can hand to any structuring method (SDD/Spec Kit, a PRD, a ticket).

It draws on established requirements-engineering practice: **elicitation** (probe tacit
needs, don't just collect stated ones), **INVEST** for sizing, **quality attributes /
NFRs**, **EventStorming** for domain logic, **Given-When-Then** acceptance criteria, and
**ADR-style** decision records.

## Core rules (both parts)

- One question at a time. Wait for the answer before the next. Many at once is bewildering.
- For every question, give your recommended answer with a one-line why — the decision is
  the user's.
- **Elicit, don't collect.** Never take the first answer as final if it hides a goal, an
  assumption, or an edge case. Probe *why* and ask for a concrete example.
- **No leading questions.** Ask what they want to achieve and how it works today — not
  "would you like X?". Never fish for confirmation of your own guess.
- Walk the decision tree by dependency: resolve what unblocks other choices first.
- Facts you can look up (files, tools, docs) — look them up. Only *decisions* go to the user.
- **Keep a running glossary.** When a domain term appears, pin one shared definition and
  reuse it (ubiquitous language).
- **Track assumptions separately from decisions.** Surface each assumption for the user to
  confirm or kill.
- Never jump to implementation or write files until told. This skill produces
  understanding, not artifacts.

## Part 1 — The Feel (what & why, never how)

Interrogate how the user should *feel* using this and what it does — not how it's built.
Stay at what/why so the solution space stays open (INVEST: negotiable). Cover, until sharp:

- Who it's for and the job they're hiring it to do — and why now.
- The primary scenarios and key moments — walk each one end to end.
- The emotional/UX target: fast? calm? powerful? guided?
- Quality attributes that decide success, as *felt* by the user: performance, reliability,
  security/privacy, accessibility, scale.
- What's deliberately out of scope.
- The success signal — how you'd know it's working.

Abstract each idea into a named functionality. Keep pulling until the set is complete and
the user confirms nothing is missing.

## Checkpoint

Play back the full list of functionalities in the user's words. Gate each against INVEST —
is it **Valuable** (clear why), **Small**, and **Testable** (you could tell if it works)?
Split or merge until each passes. Do not enter Part 2 until the user confirms the list is
complete and correct.

## Part 2 — The Build (one functionality at a time)

Take the confirmed list. Grill implementation for ONE functionality at a time, fully,
before the next.

1. **Product logic first, most thoroughly.** How it actually behaves. Model it as concrete
   scenarios — the domain events, what triggers them, what state changes (EventStorming
   style). Nail acceptance criteria in **Given / When / Then**, covering the happy path AND
   the edges: empty, invalid input, error, permission/authorization, concurrency, boundary
   states. Logic isn't done while an unanswered "what happens if…" remains.
2. **Then the mechanics** — stack, routes/endpoints, data shape, dependencies. Recommend,
   but the user chooses.
3. **Record each decision ADR-style:** the choice, a one-line rationale, and the
   alternative rejected. The rationale and the discarded option are what make it reusable.
4. **Dependency re-check.** After locking, reason out loud: does this decision create a
   downstream adjustment, open a new question, or reopen a functionality already closed?
   One decision commonly triggers more. Name it and fold it back into the queue before
   continuing. Nothing is "done" if a later decision can still reshape it.

See [references/checklists.md](references/checklists.md) for the quality-attribute catalog,
edge-case prompts, and the Given-When-Then and decision-record templates.

## Ending

When every functionality is locked and dependency-checked, synthesize in-chat: each
functionality, the experience and why behind it, its Given/When/Then acceptance criteria,
the locked implementation decisions with rationale, the open assumptions/risks, and the
glossary. Present it as reusable, method-agnostic context the user can drop into SDD/Spec
Kit or any structuring flow. Write no files. Do not start building until the user says so.
