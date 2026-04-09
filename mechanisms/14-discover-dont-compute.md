# Discover, don't compute

> When referencing filesystem state, discover it via ls/glob, never compute it from date arithmetic or assumptions.

## The mechanism

When an agent or script references filesystem state (which files exist, what data is available), discover it via `ls`/`glob`, never compute it from date arithmetic or assumptions. Computation introduces stale assumptions; filesystem discovery is ground truth.

For example, an agent that processes weekly summary files must `ls project/data/` to find available files, not calculate ISO week numbers and construct filenames.

## Why this exists

A monthly summary agent calculated which weekly files should exist using ISO week arithmetic. The calculation was wrong for edge cases (weeks spanning month boundaries, missing weeks where no data was generated). The agent crashed on files that "should" exist but didn't, and missed files that existed but weren't predicted.

## How to apply

Add to your `CLAUDE.md`:

```
Discover, don't compute -- when an agent references filesystem state (which files exist, what data is available), discover it via ls/glob, never compute it from date arithmetic or assumptions.
```

This applies to: file listings, available data ranges, configuration discovery, API endpoint enumeration. Any time the question is "what exists?" the answer should come from the filesystem, not from a calculation.
