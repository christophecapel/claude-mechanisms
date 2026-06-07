# A mechanism is not done until it is wired, measured, and self-surfacing

> A mechanism is not done when written, only when wired, measured, and self-surfacing. Verify the connection (does it fire?), the metric (how do we know it works?), and the trigger (no human memory), not just that the artifact exists.

## The mechanism

Writing a hook, gate, judge, or skill is not the same as shipping it. A mechanism is done only when three things are verified, not just that the file exists.

1. **Connection.** Is it actually registered where it runs (settings.json, a registry, a cron, a pipeline) and does it fire? A script on disk that nothing invokes is dead.
2. **Metric.** How do we know it works, and what would a regression look like? If there is no signal that proves it fires on the bad input and stays silent on the good, "working" is an assumption.
3. **Trigger.** Does it surface itself with no human having to remember? A mechanism that only runs when someone thinks to run it is a habit, not a mechanism.

"Declared" is not "firing". The default is to verify all three before calling the work done.

## Why this exists

On 2026-06-07 a hook-wiring audit ran for the first time and found three live dead hooks: a plan-before-build gate whose enforcement was silently off, a concurrent-PR gate, and a retro-routing gate that had been merged days earlier but never registered. Every artifact existed and looked done; none of them fired. The failure was not in any one hook, it was in treating "the file is written and merged" as "the mechanism is live". This principle is self-exemplifying: the audit that enforces it was verified wired before the principle itself was promoted.

## How to apply

Add to your `CLAUDE.md`:

```
A mechanism is not done until it is wired, measured, and self-surfacing. Writing a
hook/gate/judge/skill is not shipping it. Verify the connection (is it registered and
does it fire?), the metric (how do we know it works, what is a regression?), and the
trigger (does it surface itself with no human remembering?), not just that the file exists.
```

Back this with a wiring audit that walks a registry of every mechanism that must be live, and asserts each is actually connected where it runs (for hooks: present in settings.json), that registry pointers resolve to real files, and that no mechanism-shaped script is missing from the registry. Run it at session start so dead wiring surfaces itself.
