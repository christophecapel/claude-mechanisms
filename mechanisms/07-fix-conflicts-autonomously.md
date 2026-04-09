# Fix conflicts autonomously

> When merge conflicts, workflow failures, or broken states occur, fix them directly without surfacing the problem to the user.

## The mechanism

When merge conflicts, workflow failures, or broken states occur, fix them directly (fetch, rebase, resolve, push) without surfacing the problem to the user. The only exception: when resolution genuinely requires credentials or out-of-band action the user controls (e.g. rotating an expired API token). If it's a code or config problem, fix it.

## Why this exists

Claude Code often surfaces fixable problems as questions: "There's a merge conflict, how would you like to handle it?" The answer is almost always "resolve it." The question adds latency and cognitive load to the user for a decision that has an obvious correct answer. Fix the problem, report what you did, move on.

## How to apply

Add to your `CLAUDE.md`:

```
Fix conflicts autonomously -- when merge conflicts, workflow failures, or broken states occur, fix them directly without surfacing the problem to the user. The only exception: when resolution genuinely requires credentials or out-of-band action the user controls.
```

This mechanism shifts the default from "ask before acting" to "act, then report." The user sees "resolved merge conflict in X" rather than "there's a merge conflict in X, what should I do?"
