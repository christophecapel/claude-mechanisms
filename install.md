# Installation

## Option 1: Copy individual mechanisms

Each mechanism in the [mechanisms/](mechanisms/) directory is self-contained. Open the one you want, copy the text under "The mechanism," and paste it into your `CLAUDE.md` or project configuration file.

## Option 2: Copy all mechanisms

Clone this repo and copy the full set into your project:

```bash
git clone https://github.com/christophecapel/claude-mechanisms.git
```

Then reference the mechanisms directory from your `CLAUDE.md`:

```markdown
## How We Work

See mechanisms/ for the full set of operating principles.
```

## Option 3: Install as a Claude Code plugin

```bash
git clone https://github.com/christophecapel/claude-mechanisms.git ~/.claude/plugins/claude-mechanisms
```

This installs all 15 mechanisms as a Claude Code plugin. They'll be available in every session automatically.

## Customization

These mechanisms are opinionated. They reflect how one person works with Claude Code. Fork the repo, remove what doesn't fit, add your own. The format is simple:

```markdown
# [Mechanism Name]

> [One-line summary]

## The mechanism
[What to do and when]

## Why this exists
[What failure prompted this]

## How to apply
[Practical usage]
```
