# One branch, one scope

> Once a PR is presented as ready, that branch is frozen. Before committing, verify the branch matches the scope.

## The mechanism

Two rules, one principle:

1. **No late additions**: Once a PR is presented as ready to merge, that branch is frozen. If new work emerges, create a new branch and a new PR. Pushing to an in-flight PR after saying "go merge" creates a race condition where the user merges before new commits land, silently losing work.

2. **No cross-commits**: Before committing, verify the current branch matches the scope of work. If the branch belongs to a different session or feature, switch to or create the correct branch first. Committing cross-scope changes creates revert noise, merge conflicts between independent branches, and scope contamination.

## Why this exists

Two incidents from the same parallel-session workflow:

- A PR was marked ready. While the user reviewed it, an additional commit was pushed to the branch. The user merged before the new commit landed. The work was silently lost.
- A commit landed on the wrong branch during a parallel session. The cross-scope commit created a merge conflict between two branches that should have been independent.

## How to apply

Add to your `CLAUDE.md`:

```
One branch, one scope. No late additions, no cross-commits. -- once a PR is ready, the branch is frozen. Before committing, verify the branch matches the scope. New work gets a new branch and PR.
```

Pair with a pre-commit check: `git branch --show-current` before any `git add`. Enforce with a pre-push gate that blocks pushes to branches with already-merged PRs.
