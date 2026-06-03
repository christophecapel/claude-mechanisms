# Plan before build

> Before writing or editing substantive code there must be an approved plan covering that work. Reading and exploration are unrestricted; the gate is on building. Obvious one-line or mechanical fixes are exempt.

## The mechanism

Before you write or edit substantive code (scripts, tests, CI, config-as-code), there must be an approved plan covering that work.

1. Reading and exploration are unrestricted. Investigate freely.
2. The gate is on building, not on understanding.
3. Anything that adds behaviour, creates a new file, or touches a pipeline goes through plan mode first.
4. Obvious one-line or mechanical fixes are exempt.

"Build fast, review at PR" trades thoroughness for speed and has repeatedly shipped under-scrutinised work. The plan is where scope, cascade, and verification get thought through before any code exists, while changing direction is still cheap.

## Why this exists

A session built a session-start gate by editing `git-workflow-gate.py` directly with no plan. The user's correction was direct: anything to be built should be planned first. Building straight into a critical shared file skipped the step where the blast radius and the verification approach get examined.

## How to apply

Add to your `CLAUDE.md`:

```
Plan before build. Before writing or editing substantive code (scripts, tests, CI,
config-as-code) there must be an approved plan covering that work. Reading and
exploration are unrestricted; the gate is on building. One-line and mechanical fixes
are exempt; anything that adds behaviour, a new file, or touches a pipeline plans first.
```

Unlike the semantic judgment of mechanism #24, this is a structural check, so it is enforced by `plan-before-build-gate.py`, a deterministic hard-block PreToolUse hook with a user-only `CLAUDE_PLAN_GATE_OFF` escape hatch.
