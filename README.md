# claude-mechanisms

![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)
![Mechanisms](https://img.shields.io/badge/Mechanisms-15-blue.svg)
![Built for](https://img.shields.io/badge/Built%20for-Claude%20Code-orange.svg)

> Mechanisms, not rules. Triggers, not intentions. Built for Claude Code.
>
> "Good intentions don't work. Mechanisms do." -- Jeff Bezos

15 mechanisms codified from working with Claude Code every day. Distilled into the operating principles that actually stuck.

Not rules (rules get forgotten between sessions). Not principles (too abstract to enforce). **Mechanisms** -- with triggers, retry logic, and failure notifications that fire whether you remember them or not.

## Why mechanisms, not rules?

Early on, when something went wrong, I'd ask Claude to prevent it happening again. It would write a rule or save a note in memory. Next session? Gone. So I started thinking harder about what actually sticks.

A mechanism has:
- A **clear trigger** (not manual memory)
- **Consistent execution** when the trigger fires
- A **defined expected outcome**
- **Retry logic** (up to N attempts) when the outcome isn't met
- A **failure notification** if retries are exhausted -- never fail silently

## The 15 mechanisms

| # | Mechanism | One-liner |
|---|---|---|
| 01 | [Read before creating](mechanisms/01-read-before-creating.md) | Check if a file exists before writing a new one |
| 02 | [git mv, not cp + rm](mechanisms/02-git-mv-not-cp-rm.md) | Preserve history when moving files |
| 03 | [No orphaned files](mechanisms/03-no-orphaned-files.md) | If content migrates, delete the source |
| 04 | [One focused thing per session](mechanisms/04-one-focused-thing-per-session.md) | Resist scope creep |
| 05 | [Auto-derive, don't ask](mechanisms/05-auto-derive-dont-ask.md) | Use inferable data, don't ask for it |
| 06 | [Deferred work needs persistent markers](mechanisms/06-deferred-work-needs-persistent-markers.md) | Write flags, not verbal promises |
| 07 | [Fix conflicts autonomously](mechanisms/07-fix-conflicts-autonomously.md) | Fix it directly, don't surface the problem |
| 08 | [Build mechanisms, not habits](mechanisms/08-build-mechanisms-not-habits.md) | The meta-mechanism that defines all others |
| 09 | [Incremental rollout, not big-bang swap](mechanisms/09-incremental-rollout-not-big-bang-swap.md) | Add alongside, verify, then remove the old |
| 10 | [Atomic credential persistence](mechanisms/10-atomic-credential-persistence.md) | Persist replacements before doing any other work |
| 11 | [Parity over independence](mechanisms/11-parity-over-independence.md) | Test that N things work the same, not just individually |
| 12 | [One PR, one scope, no late additions](mechanisms/12-one-pr-one-scope-no-late-additions.md) | Once presented as ready, the branch is frozen |
| 13 | [Branch = scope boundary](mechanisms/13-branch-equals-scope-boundary.md) | Verify the branch matches the work before committing |
| 14 | [Discover, don't compute](mechanisms/14-discover-dont-compute.md) | Use filesystem discovery, not date arithmetic |
| 15 | [Consolidate review in the artifact](mechanisms/15-consolidate-review-in-artifact.md) | Put proposed changes inside the file, not in chat |

## Quick start

**Option 1: Copy what you need**

Browse the [mechanisms/](mechanisms/) directory. Each file is self-contained. Copy any mechanism into your own `CLAUDE.md` or project configuration.

**Option 2: Install as a Claude Code plugin**

```bash
git clone https://github.com/christophecapel/claude-mechanisms.git ~/.claude/plugins/claude-mechanisms
```

## About

Built by [Christophe Capel](https://github.com/christophecapel) -- a product leader building a personal operating system with Claude Code and codifying the discipline that makes it work.

These mechanisms emerged from real failures: wrong-branch commits, lost credentials, orphaned files, scope creep across parallel sessions, and rules that Claude forgot between conversations. Each one exists because something broke and I made sure it wouldn't break the same way twice.

If any of these save you time, I want to hear about it. If you have mechanisms of your own, open a PR or an issue.

## License

MIT
