# One focused thing per session

> Mixing concerns inflates blast radius and muddies git history. Resist scope creep.

## The mechanism

Each Claude Code session should have one clear objective. When a second concern surfaces during work, note it as a deferred item (see mechanism #6) rather than tackling it immediately. Finish the original scope, commit, then decide whether to start a new session for the second concern.

## Why this exists

Claude Code sessions that mix concerns produce commits that are hard to review, hard to revert, and hard to explain in git history. A "quick fix" to an unrelated file during a feature session creates a commit that touches both the feature and the fix. If either needs to be reverted, the other comes with it.

## How to apply

Add to your `CLAUDE.md`:

```
One focused thing per session -- mixing concerns inflates blast radius and muddies git history. Resist scope creep.
```

This is a discipline mechanism, not a hard gate. The trigger is noticing you're about to touch something outside the session's original scope. The action is to write a deferred marker instead.
