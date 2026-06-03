# Unblock the parallel path before your own serial work

> When an action will make someone wait (a commit, a long build, a sequential dependency), first identify and hand off any work that can run concurrently, then do your blocking work. Optimize for others' wall-clock throughput, not your local task order.

## The mechanism

Before you start a step that makes the user or another session wait, ask whether there is work they could be doing in parallel right now. If there is, hand it off first.

1. Identify the blocking action (a push, a long build, a sequential dependency that gates others).
2. Identify any concurrent work that does not depend on it: a brief to write, a task to start, an interface to build against.
3. Hand that off first, then do your blocking work.

In a multi-session build the same rule applies to shared interfaces: lock and hand off the shared contract before building your own consumer of it, so the other session is never blocked waiting on an interface only you can see.

## Why this exists

A session blocked the user on committing post #09 before doing anything else, when it could have first handed off the banner brief and the LinkedIn-post briefs for the user to run in parallel. The serial ordering was locally convenient but cost the user wall-clock time they did not need to lose.

Separately, within a multi-session build, one session built its own consumer of a shared interface before locking and handing off that interface, leaving the parallel session blocked on a contract it could not yet see.

Both share a root cause: optimizing for the local task order instead of total throughput across everyone who is waiting.

## How to apply

Add to your `CLAUDE.md`:

```
Unblock the parallel path before your own serial work. When an action will make
the user or another session wait, first identify and hand off any work they can do
concurrently (a brief, a task, an interface to build against), then do your blocking
work. Optimize for others' wall-clock throughput, not your local task order.
```

This is semantic judgment, not a structural check, so it is enforced via the shared judge class `serial_work_before_parallel_dispatch` (registered in `judge-registry.yaml` and `docs/judge-engine.md`), not a deterministic hook.
