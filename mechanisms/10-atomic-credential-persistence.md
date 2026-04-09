# Atomic credential persistence

> When consuming a single-use credential, persist the replacement immediately before doing any other work. If persistence fails, abort.

## The mechanism

When an operation consumes a single-use credential (OAuth refresh token, one-time code), persist the replacement immediately before doing any other work. If persistence fails, abort. Never proceed with work that depends on a credential you haven't saved. If multiple workflows share the same credential, enforce mutual exclusion (concurrency groups, locks).

## Why this exists

A Fitbit OAuth integration consumed a single-use refresh token during a backfill operation. The backfill crashed before persisting the new token. Both the daily workflow and the backfill workflow died holding dead credentials. The fix wasn't just "save the token first" -- it was recognizing that single-use credentials require atomic handling: consume, persist replacement, then proceed. Any other order risks bricking the integration.

## How to apply

Add to your `CLAUDE.md`:

```
Atomic credential persistence -- when an operation consumes a single-use credential (OAuth refresh token, one-time code), persist the replacement immediately before doing any other work. If persistence fails, abort.
```

This mechanism is critical for any integration that uses OAuth 2.0 refresh tokens, one-time API keys, or rotating secrets. The pattern is: read token, use token, receive new token, persist new token, THEN do the actual work.
