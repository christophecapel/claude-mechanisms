# Auto-derive, don't ask

> If data is inferable from context, use it. Ask only when genuinely ambiguous. One question, not several.

## The mechanism

Before asking the user a question, check whether the answer is already available in the codebase, git history, file names, directory structure, or prior conversation. If it is, use it directly. If you must ask, ask one question, not a list.

## Why this exists

Claude Code tends toward politeness over efficiency, asking for confirmation on things it could derive. "What should I name this file?" when there's an obvious naming convention. "Which directory?" when the project structure makes it clear. Each unnecessary question breaks the user's flow and adds round-trip latency to the session.

## How to apply

Add to your `CLAUDE.md`:

```
Auto-derive, don't ask -- if data is inferable from context, use it. Ask only when genuinely ambiguous. One question, not several.
```

The boundary is "genuinely ambiguous." If two reasonable people would give different answers, ask. If the answer is obvious from context, derive it.
