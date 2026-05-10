# Contributing to claude-mechanisms

This repo is the catalog of operating mechanisms for Claude Code — the **why** that pairs with [`claude-mechanisms-tools`](https://github.com/christophecapel/claude-mechanisms-tools)'s **how**.

A mechanism here describes a recurring failure mode and the structural intervention that prevents it. Not a rule. Not a principle. A trigger + retry logic + failure path.

## Before opening a PR

1. **Real failure first.** Mechanisms are extracted from real failures, not theorised. Document the failure mode, when it happened, and the evidence it recurred.
2. **Structural, not behavioral.** If the proposed mechanism is "remember to X" or "always do Y," it's a behavioral rule and won't stick under cognitive load. Look for a structural intervention: hook, gate, lifecycle pattern, or process change.
3. **Pair with implementation when possible.** Most mechanisms here have a corresponding tool in `claude-mechanisms-tools` that enforces them. If your mechanism doesn't have a tool yet, that's fine — flag it as `[no implementation yet]` in the manifest.

## Mechanism file shape

Each mechanism lives at `mechanisms/NN-short-title.md` with this structure:

```markdown
# Title (matches "name" in mechanisms.yaml)

> One-sentence summary.

## The mechanism

What the mechanism is. Trigger, retry, failure path.

## Why this exists

The real failure mode that prompted it. Specific incidents are stronger than abstract reasoning.

## How to apply

What to add to your `CLAUDE.md` or workflow. Concrete, copy-pasteable.

## Implementations

| Tool | Repo | Kind | Introduced |
|---|---|---|---|
| ... |
```

The `## Implementations` table cross-links to tools in `claude-mechanisms-tools`. Every entry in `mechanisms.yaml`'s `implementations:` field must resolve to a real path in the toolkit at HEAD.

## Adding a mechanism

1. Pick the next free ID (max existing ID + 1)
2. Create `mechanisms/NN-name.md` following the structure above
3. Add an entry to `mechanisms.yaml` with `id`, `name`, `file`, `scope`, and (if applicable) `implementations:`
4. Add a row to the table in `README.md`
5. Add a `CHANGELOG.md` entry
6. If there's a paired tool, open a PR in `claude-mechanisms-tools` referencing the new mechanism

## Improving an existing mechanism

Be careful with renumbering. The numbers are stable identifiers used by `tools.yaml` `mechanism_ids:` arrays in the toolkit. If a mechanism gets superseded, mark it deprecated rather than deleting it.

## PR shape

Bundle the mechanism file, manifest entry, README row, and CHANGELOG entry in a single commit. Use the PR template.

## Reporting bugs / proposing mechanisms

Use the issue templates. There's a dedicated `mechanism_proposal.md` template for new mechanism ideas.

## Code of conduct

See [`CODE_OF_CONDUCT.md`](CODE_OF_CONDUCT.md). Contributor Covenant 2.1.
