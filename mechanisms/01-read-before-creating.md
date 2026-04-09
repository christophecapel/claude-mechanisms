# Read before creating

> Check if a file already exists before writing a new one. Avoid duplication.

## The mechanism

Before creating any new file, check whether a file with the same purpose already exists. Search by name, by content pattern, and by location. If a match exists, extend or update it rather than creating a duplicate.

## Why this exists

Claude Code defaults to creating new files when asked to add something. Over weeks of daily use, this leads to file bloat: three versions of the same config, duplicate utility functions, competing READMEs. Each duplicate is a future merge conflict and a source of confusion about which version is canonical.

## How to apply

Add to your `CLAUDE.md`:

```
Read before creating -- check if a file already exists before writing a new one. Avoid duplication.
```

This is one of the simplest mechanisms and one of the most impactful. It applies to every file type: code, config, documentation, data.
