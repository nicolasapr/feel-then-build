# feel-then-build

A Claude Code plugin with one skill: **`feel-then-build`** — a relentless, two-part
interview for scoping a new feature while you keep every decision. It writes no files and
no code; the output is a shared understanding you can hand to any structuring method
(SDD/Spec Kit, a PRD, a ticket).

It follows the style of Matt Pocock's `grill-*` skills: one question at a time, a
recommended answer for each, facts looked up from the environment, decisions left to you.

## The two phases

1. **The Feel** — how you should *feel* using it and what it does. Pure functionality and
   abstraction. No stack, no routes, no data model.
2. **Checkpoint** — the skill plays back the full list of functionalities and waits for
   your confirmation before going further.
3. **The Build** — one functionality at a time: product logic first (behavior, edge
   cases, states, rules), then stack, routes, data. After locking each one, it reasons
   whether that decision creates a downstream adjustment or reopens something already
   closed, and folds it back into the queue.
4. **Ending** — an in-chat synthesis you can drop into your structuring flow. No files
   written, no code started until you say so.

## Install

```
/plugin marketplace add nicolasapr/feel-then-build
/plugin install feel-then-build@nicolas
```

Then run it with:

```
/feel-then-build
```

The skill is user-invoked only (`disable-model-invocation: true`) — Claude will not
auto-trigger it.

## Layout

```
.claude-plugin/
  marketplace.json    # marketplace entry
  plugin.json         # plugin metadata
skills/
  feel-then-build/
    SKILL.md          # the skill
```

## License

MIT — see [LICENSE](LICENSE).
