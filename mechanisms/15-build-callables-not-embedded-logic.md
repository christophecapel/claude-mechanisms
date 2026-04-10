# Build callables, not embedded logic

> When logic will be needed from more than one context, extract it into a standalone script with CLI args from day one.

## The mechanism

When a piece of logic will be needed from more than one context (workflow, agent, manual invocation, backfill), extract it into a standalone script with CLI args from day one.

The test: "If I need this in a second place tomorrow, would I import or copy-paste?" If copy-paste, the design is wrong.

## Why this exists

A reconciliation routine was initially proposed as embedded logic inside an agent prompt file. The user pushed back: "What about backfill? What about ad-hoc changes?" Result: one Python script called from 4 places (daily workflow, session agent, backfill workflow, and manual CLI) with identical behaviour everywhere. The embedded version would have required duplicating the logic into each caller.

## How to apply

Add to your `CLAUDE.md`:

```
Build callables, not embedded logic -- when logic will be needed from >1 context, extract it into a standalone script with CLI args from day one. One script, multiple callers, same behaviour.
```

During planning, count the callers. If more than one exists or is foreseeable, build a script with standard flags (`--date`, `--from/--to`, `--dry-run`). Agent prompts invoke the script; they don't contain the logic.
