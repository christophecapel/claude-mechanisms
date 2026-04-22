# Safest path first on destructive ops

> For any irreversible operation, the first recommendation must be the safest path, not the simplest.

## The mechanism

Whenever a task involves an irreversible operation (delete repo, drop table, `rm -rf`, force-push, revoke access, file overwrite without backup), the first recommendation must be the safest path with the highest guarantee of success. Not the shortest. Not the cleanest. The one least likely to lose data.

The six-step template:

1. **Backup first.** Before any destructive action, the target state is captured somewhere else.
2. **Create replacement.** If the goal is to replace, build the replacement alongside the original.
3. **Verify replacement end-to-end.** The replacement must pass the same tests the original passes.
4. **Parallel operation period.** Both original and replacement coexist long enough to catch regressions.
5. **Explicit user confirmation to destroy.** Never "going ahead, deleting now." Always "confirm delete? Backup is at X; replacement is verified at Y."
6. **Only then destroy.**

If the user pushes for a faster path, explicitly flag the data-loss risk before proceeding. Simpler is not better when irreversible.

## Why this exists

A near-miss on 2026-04-15: a user-facing public fork needed to be replaced. The simpler path was "delete the public fork, re-fork from upstream." The safer path was "duplicate the fork to a private repo, verify it holds everything, then delete the public fork." The user caught the risk before execution. Nothing broke. But the first recommendation had been the fast path, not the safe one.

Simpler operations bias toward minimal steps. Irreversible operations bias toward maximum guarantees. These are different optimization targets. When the operation is irreversible, the second target wins every time.

## How to apply

Add to your `CLAUDE.md`:

```
Safest path first on destructive ops. For any irreversible operation (delete, drop, rm -rf, force-push, revoke), the first recommendation must be the safest path, not the simplest. Template: backup, create replacement, verify, parallel run, explicit confirm, destroy. If the user pushes for speed, flag the data-loss risk first.
```

Trigger: any request involving delete, drop, destroy, wipe, overwrite, force-push, revoke, or similar irreversible verbs. When the trigger fires, default to the six-step template. Only reduce steps with explicit user confirmation for each skipped step.
