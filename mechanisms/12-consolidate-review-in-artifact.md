# Consolidate review in the artifact

> When iterating on any reviewable artifact, write the proposed next version into the artifact itself with inline markers per change.

## The mechanism

When iterating on any reviewable artifact (draft, document, plan, code, email, spec), write the proposed next version into the artifact itself with inline decision markers per change. Do not split proposals between chat and the file. The reviewer should never have to mentally merge two sources to see the result. Chat is for direction and trade-off calls; the artifact is the source of truth.

Exceptions: pure A/B decisions before any artifact exists, exploratory brainstorming, and one-line tweaks where the round-trip costs more than it saves.

## Why this exists

During a content iteration session, proposed text changes were described in chat while the file still held the old version. The reviewer had to read chat, hold the proposal in working memory, switch to the editor, mentally simulate the merged result, then switch back to chat to react. This is high cognitive load, especially across multiple revision cycles.

## How to apply

Add to your `CLAUDE.md`:

```
Consolidate review in the artifact -- when iterating on any reviewable artifact, write the proposed next version into the artifact itself with inline decision markers per change. Do not split proposals between chat and file.
```

Use inline HTML comments for decision markers: `<!-- DECISION N: what changed, why, ACCEPT / TWEAK / REJECT? -->`. Mark unchanged blocks with `<!-- KEPT -->` so the reviewer doesn't have to wonder whether something was missed.
