# Build mechanisms, not habits

> Every recurring action must have a clear trigger, consistent execution, a defined outcome, retry logic, and a failure notification.

## The mechanism

Every recurring action must have:
1. A **clear trigger** (not manual memory)
2. **Consistent execution** when the trigger fires
3. A **defined expected outcome**
4. **Retry logic** (up to N attempts) when the outcome isn't met
5. A **failure notification** if retries are exhausted -- never fail silently

If an action relies on someone remembering to do it, it's a habit, not a mechanism. Habits degrade under load. Mechanisms fire regardless.

## Why this exists

This is the meta-mechanism. It defines the standard all other mechanisms in this collection meet. It emerged from noticing that "I'll remember to do X next time" is a lie the brain tells itself. The system needs to remember, not the person.

## How to apply

Add to your `CLAUDE.md`:

```
Build mechanisms, not habits -- every recurring action must have: (a) a clear trigger (not manual memory), (b) consistent execution when the trigger fires, (c) a defined expected outcome, (d) retry logic (up to N attempts) when the outcome isn't met, (e) a failure notification if retries are exhausted -- never fail silently.
```

When you notice yourself saying "I need to remember to..." or "next time I should...", that's the trigger to build a mechanism instead of making a mental note.
