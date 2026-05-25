# Unit-test the parts, then end-to-end-test the whole

> Per-component unit tests AND a final end-to-end integration run against real state. A green unit suite or a passing gate is not a substitute for running the thing.

## The mechanism

Any multi-component change ships with both layers:

1. **Per-component unit tests** as each piece lands.
2. **A final end-to-end integration run** of the assembled system against real state, before it's called done.

A green unit suite proves each piece is built right. A passing structural or review gate proves each piece meets its contract. Neither proves the *assembled system actually works*. Only the end-to-end run does that.

This extends to multi-step recovery, backup, and fallback flows: test each step in isolation AND the full path end-to-end. A recovery path that has never executed end-to-end is unverified. Treat it as broken until a real run (or a forced-failure test) proves it fires.

## Why this exists

A large refactor once shipped ~18 child changes, each with green unit tests and a passing structural gate. The assembled system was never actually run. A single end-to-end invocation immediately surfaced three real gaps that every unit test and the gate had passed straight over: a false-flagging detector, an artifact that was never generated, and a report that was never produced.

Separately, a scheduled pipeline carried a recovery fallback that had been silently disabled for nine weeks: its required credential was never wired into the workflow. The happy path always worked, so nothing surfaced the break until the day the fallback was actually needed, and it wasn't there.

Both failures share a root cause: confidence drawn from component-level green, with no test of the whole.

## How to apply

Add to your `CLAUDE.md`:

```
Unit-test the parts, then end-to-end-test the whole. Multi-component work ships
with per-component unit tests AND a final end-to-end integration run against real
state before it's done. A green suite or passing gate is not a substitute for
running the assembled system. For multi-step recovery/backup/fallback flows, test
each step AND the full path end-to-end. An untested recovery path is unverified.
```

Make the final end-to-end run the explicit last checklist item on every multi-part epic. If a live run genuinely isn't possible, say so plainly rather than substituting "tests pass + gate green" for "it works."
