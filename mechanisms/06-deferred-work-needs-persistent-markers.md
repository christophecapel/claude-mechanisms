# Deferred work needs persistent markers

> Verbal instructions to "do it next time" vanish between sessions. Write a flag; detect the flag at session start.

## The mechanism

When work is deferred to a future session, write a persistent marker: a TODO comment in the relevant file, a `[deferred]` tag in a tracking document, or an issue in your project tracker. The marker must be detectable at the start of the next session without requiring anyone to remember it was deferred.

## Why this exists

Claude Code sessions are stateless. A verbal "we'll handle this tomorrow" in today's session is gone tomorrow. Without a persistent marker, deferred work only resurfaces when the underlying problem bites again, often at the worst possible time.

## How to apply

Add to your `CLAUDE.md`:

```
Deferred work needs persistent markers -- verbal instructions to "do it next time" vanish between sessions. Write a flag (TODO, [deferred] tag); detect the flag at session start.
```

Pair with a session-start routine that scans for deferred markers. The mechanism has two parts: the write (when deferring) and the read (when starting).
