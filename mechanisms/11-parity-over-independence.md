# Parity over independence

> When consolidating N things into a shared base, the critical test is parity across the N things, not correctness of each in isolation.

## The mechanism

When consolidating N things into a shared base, the critical test is parity across the N things, not correctness of each in isolation. Independent tests prove each works; parity tests prove they work the same way. Always add cross-component assertions (e.g. "all dashboards have timestamp, subtitle, calendar labels"). Drift between siblings is invisible to per-component tests.

## Why this exists

During a dashboard consolidation, each individual dashboard passed its own tests. But they had drifted: one had timestamps, another didn't; one had calendar labels, another used a different format. Per-component tests couldn't catch this because they only tested "does this component work?" not "do all components work the same way?"

## How to apply

Add to your `CLAUDE.md`:

```
Parity over independence -- when consolidating N things into a shared base, the critical test is parity across the N things, not correctness of each in isolation.
```

This applies to: dashboards, API endpoints, config files, agent prompts, test suites, documentation. Anywhere you have multiple instances of the same pattern, add a parity assertion that checks they all conform.
