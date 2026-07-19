# Checklists & Templates

Deeper reference for `feel-then-build`. Pull from these only as needed — the main SKILL.md
carries the flow; this file is the catalog you draw questions from so no dimension is
silently skipped.

## Contents

- [Part 1 — elicitation coverage](#part-1--elicitation-coverage)
- [Quality attributes (NFR) catalog](#quality-attributes-nfr-catalog)
- [Part 2 — product-logic edge-case prompts](#part-2--product-logic-edge-case-prompts)
- [Given-When-Then template](#given-when-then-template)
- [Decision-record template (ADR-lite)](#decision-record-template-adr-lite)

## Part 1 — elicitation coverage

Requirements can't just be *collected* — they must be *elicited*, because stakeholders hold
tacit knowledge they won't volunteer. Use these angles (after Alexander & Beus-Dukic) to
make sure Part 1 is complete:

- **Stakeholders** — who uses it, who is affected, who decides, who maintains it.
- **Goals** — the outcome behind the request. Ask "why" until you hit a real objective.
- **Context** — where/when it's used, on what device, alongside what other tools.
- **Scenarios** — concrete end-to-end walkthroughs of the main moments, not abstractions.
- **Qualities & constraints** — the non-functional bar (see catalog below).
- **Rationale & assumptions** — what the user is assuming is true; mark each to confirm.
- **Definitions** — terms that carry domain meaning; pin one shared definition (glossary).
- **Priorities** — what's essential vs nice-to-have vs explicitly out.

Anti-pattern to avoid: leading questions. Prefer "How do you handle this today?" and
"Walk me through the last time you needed this" over "Wouldn't it be nice if…?".

## Quality attributes (NFR) catalog

"Functional requirements define what a system does; non-functional requirements define how
it must *be*." These often decide success or failure. Ask which ones matter and to what
measurable bar — skip the ones that genuinely don't apply.

- **Performance / latency** — acceptable response time, throughput, under what load.
- **Scalability** — expected volume now and at 10x; concurrent users.
- **Reliability / availability** — uptime target, failure tolerance, data-loss tolerance.
- **Security** — authentication, authorization, threat model, sensitive data handling.
- **Privacy / compliance** — PII, retention, regulations (GDPR/LGPD, etc.).
- **Usability / accessibility** — a11y standard, localization, learnability.
- **Maintainability** — who maintains it, how changes ship.
- **Observability** — logging, metrics, how you'll know it broke.
- **Cost** — infra/budget ceilings that constrain the design.
- **Portability / compatibility** — browsers, OSes, offline, integrations.

## Part 2 — product-logic edge-case prompts

For every functionality, don't declare the logic done until each of these has an answer or
an explicit "not applicable":

- **Empty** — first run, no data, nothing selected.
- **Invalid input** — bad format, out of range, malicious.
- **Error** — dependency down, timeout, partial failure. What does the user see/do?
- **Permission** — unauthenticated, wrong role, ownership boundaries.
- **Concurrency** — two actors act at once; race conditions; double submit.
- **Boundaries** — min/max, first/last, very large, very small.
- **State transitions** — every state and every legal/illegal transition between them.
- **Lifecycle** — create, read, update, delete, archive; who can do each and when.
- **Idempotency / retries** — what happens if the same action fires twice.

Model the flow as domain **events** ("OrderPlaced"), the **commands** that trigger them,
and the **state** that changes (EventStorming). Gaps between events reveal missing logic.

## Given-When-Then template

Write acceptance criteria as observable behavior, in the shared/ubiquitous language:

```
Scenario: <short name>
  Given <initial context / state>
  When  <action or event>
  Then  <observable outcome>
```

Add one scenario per branch that matters (happy path + each relevant edge above). If you
can't phrase a Then as something observable, the functionality isn't yet Testable.

## Decision-record template (ADR-lite)

Capture each Part 2 decision so it survives handoff. Keep one record per decision.

```
Decision: <the choice made>
Context:  <why this came up; what constrains it>
Rationale: <why this option>
Alternatives rejected: <options considered and why not>
Consequences: <what this now forces or enables; follow-up decisions it triggers>
```

A single decision commonly triggers further decisions — list those under Consequences and
feed them back into the interview queue rather than losing them.
