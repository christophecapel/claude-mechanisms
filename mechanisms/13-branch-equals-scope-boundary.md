# Branch = scope boundary, never cross-commit

> Before committing, verify the current branch matches the scope of work.

## The mechanism

Before committing, verify the current branch matches the scope of work. If the branch belongs to a different session or feature, switch to or create the correct branch first. Committing cross-scope changes to another branch creates revert noise, merge conflicts between branches that should be independent, and scope contamination the user has to untangle.

## Why this exists

During a parallel session workflow, a commit landed on the wrong branch. The branch belonged to a different feature being worked on in a separate Claude Code session. The cross-scope commit created a merge conflict between two branches that should have been independent. Untangling it took longer than the original work.

## How to apply

Add to your `CLAUDE.md`:

```
Branch = scope boundary, never cross-commit -- before committing, verify the current branch matches the scope of work. If the branch belongs to a different session or feature, switch to or create the correct branch first.
```

Pair with a pre-commit check: `git branch --show-current` before any `git add` or `git commit`. This is especially critical when running multiple Claude Code sessions in parallel.
