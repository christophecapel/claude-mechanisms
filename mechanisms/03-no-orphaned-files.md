# No orphaned files

> If content migrates, delete the source. No redirects nobody reads.

## The mechanism

When content moves from one file to another, delete the original. Do not leave behind a stub, a redirect note, or a "this has moved to..." comment. The new location is the only location.

## Why this exists

During refactors and reorganizations, Claude Code tends to create the new file but leave the old one "just in case." Within a week, nobody remembers which version is current. Both get edited independently. The orphan becomes a source of stale information that looks authoritative because it still exists.

## How to apply

Add to your `CLAUDE.md`:

```
No orphaned files -- if content migrates, delete the source. No redirects nobody reads.
```

Pair this with mechanism #2 (git mv) when possible. If the move is a true rename, `git mv` handles both the creation and deletion in one step.
