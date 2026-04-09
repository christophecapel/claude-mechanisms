# git mv, not cp + rm

> Always use `git mv` when moving files. Preserves history (R100 rename detection).

## The mechanism

When moving or renaming a file, always use `git mv` instead of copying to the new location and deleting the old one. This preserves the file's full commit history through Git's R100 rename detection.

## Why this exists

Claude Code often handles file moves as a copy + delete sequence. This breaks `git log --follow` for the moved file, making it impossible to trace its history. For files with significant evolution (configs, core modules, documentation), losing history means losing the context behind every decision that shaped the file.

## How to apply

Add to your `CLAUDE.md`:

```
git mv, not cp + rm -- always use git mv when moving files. Preserves history (R100 rename detection).
```

This is especially important for files that have been iterated on heavily. A file with 50 commits of history becomes a file with 1 commit of history after a cp + rm move.
