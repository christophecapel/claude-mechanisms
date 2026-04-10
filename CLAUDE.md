# claude-mechanisms

A public collection of 16 operating mechanisms for Claude Code. Each mechanism is a self-contained markdown file in `mechanisms/`.

## Folder structure

- `mechanisms/` -- one `.md` file per mechanism, numbered 01-16
- `README.md` -- overview, table of contents, install instructions
- `CHANGELOG.md` -- versioned changes with rationale
- `install.md` -- detailed plugin installation guide

## Standards

- Each mechanism file has 4 sections: summary, the mechanism, why this exists, how to apply
- No em dashes -- use commas, periods, or "not" constructions
- Mechanism numbering may change during consolidation passes (document in CHANGELOG.md)
- Every mechanism must have a real origin story (what failure prompted it)
- Every shape change (add/remove/merge) requires a version tag + GitHub release
