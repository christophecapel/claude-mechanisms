# Incremental rollout, not big-bang swap

> Add the new thing alongside the old thing, verify it works, then remove the old thing. Never swap in one step.

## The mechanism

When changing an integration, endpoint, or data source: add the new thing alongside the old thing, verify it returns valid data in a real run, then remove the old thing. Never swap in one step. Add a smoke test or validation gate that runs before the main operation. "Run it manually to check" is a habit, not a mechanism (see mechanism #8).

## Why this exists

Big-bang swaps fail silently. You replace the old API endpoint with the new one, the new one returns slightly different data, and downstream processes break in ways you don't notice until hours or days later. The incremental approach guarantees a comparison point: you can diff old vs. new output before cutting over.

## How to apply

Add to your `CLAUDE.md`:

```
Incremental rollout, not big-bang swap -- when changing an integration, endpoint, or data source: add the new thing alongside the old thing, verify it returns valid data in a real run, then remove the old thing. Never swap in one step.
```

This applies to code, configuration, infrastructure, and data pipelines. Any place where "the old way" and "the new way" can coexist temporarily, they should.
