# Hooks silent on pass

> Any hook or gate emits nothing on a clean pass. Block-class events deny with full actionable detail. Warn-class events emit one short line.

## The mechanism

A hook's job is to catch failures, not to confirm successes. When a check passes cleanly, the hook prints nothing. When a check blocks, it denies with the full actionable detail needed to fix the problem. When a check warns, it emits one short line.

Why silent on pass matters: hook stdout becomes `additionalContext` fed back into the model on every subsequent turn. A hook that prints a three-line "all green" checklist on every pass is not informative, it is a persistent tax on every future turn in the session. Over a long session with dozens of hook invocations, those passive confirmations compound into thousands of tokens of noise, pushing real decisions out of context at auto-compression time.

The rule:

- **Pass:** exit 0, stdout empty.
- **Warn:** exit 0, stdout one short line describing the advisory.
- **Block:** non-zero exit, stdout full detail of what failed and how to fix.

## Why this exists

The hook-efficiency session on 2026-04-21 measured hook overhead across thirty recent sessions. Median session hook time was 7.0 seconds, 95th percentile was 51.6 seconds, max was 79.6 seconds. The dominant bleed was `info()` calls on green paths in `plan-review-gate` and `git-workflow-gate` at session-start and session-end. Verbose pass output was not helping anyone debug problems; it was paying token cost to confirm that nothing was wrong.

Green paths that still call `info()` with a checklist are a regression from this mechanism and must be reverted. The fix is one-liner: delete the `info()` call.

## How to apply

Add to your `CLAUDE.md`:

```
Hooks silent on pass. Any hook or gate emits nothing on a clean pass. Block denies with full actionable detail. Warn emits one short line. Green-path info() calls are a regression.
```

Trigger: any new or existing hook. When reviewing a hook, check: does it print anything on the happy path? If yes, the hook is inflating session token cost. Remove the pass-path output unless there is a specific reason it is actionable.
