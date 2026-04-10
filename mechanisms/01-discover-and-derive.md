# Discover and derive, never assume or ask

> Before creating a file, check if it exists. Before asking the user, check if you can derive the answer. Before computing state, discover it from the filesystem. Before proposing new tooling, check what the repo already uses.

## The mechanism

Ground truth is always cheaper than assumption. Apply this at every scope:

- **Files**: Check if a file already exists before writing a new one. Search by name, content pattern, and location.
- **Information**: Before asking the user a question, check whether the answer is in the codebase, git history, file names, or directory structure.
- **State**: When referencing filesystem state (which files exist, what data is available), discover it via `ls`/`glob`, never compute from date arithmetic or assumptions.
- **Architecture**: Before recommending new infrastructure, automation, or tooling, check what the repo already uses. The existing pattern IS the recommendation.
- **Actions**: When the obvious next action follows from derived information, execute it in the same turn. Don't ask "should I do X?" when X is clearly the right move.

## Why this exists

Three failures from the same root cause, discovered in one session:

1. Claude proposed a new scheduling tool without checking that all existing scheduled infra used GitHub Actions cron + Python scripts
2. Claude asked "have you done X?" when `git log` would have answered the question
3. Claude asked "want me to update the ticket?" when the right action was obvious from context

All three are the same principle: check before acting, derive before asking, discover before computing.

## How to apply

Add to your `CLAUDE.md`:

```
Discover and derive, never assume or ask -- before creating a file, check if it exists. Before asking the user, check if you can derive the answer. Before computing state, discover it from the filesystem. Before proposing new tooling, check what the repo already uses. Ground truth is always cheaper than assumption. Ask only when genuinely ambiguous; one question, not several.
```

This is the single highest-impact mechanism. It applies to every interaction.
