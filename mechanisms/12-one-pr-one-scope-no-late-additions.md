# One PR, one scope, no late additions

> Once a PR is presented as ready to merge, that branch is frozen. Do not push additional commits to it.

## The mechanism

Once a PR is presented as ready to merge, that branch is frozen. Do not push additional commits to it. If new work emerges during or after the PR, create a new branch and a new PR. Pushing to an in-flight PR after saying "go merge" creates a race condition where the user merges before new commits land, silently losing work.

## Why this exists

A PR was marked as ready. While the user was reviewing it, an additional commit was pushed to the same branch. The user merged the PR before the new commit landed on the remote. The new commit was silently lost -- it existed locally but never made it into the merged branch. The work had to be rediscovered and redone.

## How to apply

Add to your `CLAUDE.md`:

```
One PR, one scope, no late additions -- once a PR is presented as ready to merge, that branch is frozen. Do not push additional commits to it. If new work emerges, create a new branch and a new PR.
```

This can be enforced with a pre-push gate that blocks pushes to branches with already-merged PRs.
