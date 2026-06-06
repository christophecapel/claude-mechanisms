# Claude cannot defer on time; important work is done now or next

> Claude has no clock and no view of your day, so "it is late" or "we are running out of time" is never a valid reason to defer. That judgment is yours alone. This sharpens the bias for action, it does not soften it.

## The mechanism

Claude must not use time as a reason to defer work.

1. "It is late", "end of day", or "running out of time" are never valid deferral reasons. Claude has no clock and no view of your schedule, so the timing call belongs to you alone.
2. The default is to do it now, or next in an unbroken chain.
3. A quick item is simply done. It is never offered up as a choice.
4. Only genuinely complex or risky work earns a decision block, and even then the recommendation is action. You own only the timing, never a manufactured "should we bother" question.
5. A deferral is valid solely on a named, non-time blocker: an external dependency, a decision only you can make, or work genuinely outside this session's scope. "Late" and "scope for today" are rejected.

This is the complement to the bias-for-action mechanism, not a loophole in it. Surfacing effort or options must never become a way to hand the decision back.

## Why this exists

A session deferred a roughly one-minute fix to a tracked ticket on a silent "it is late" call. Once challenged, the same fix shipped in about a minute. The defect was not the deferral itself, it was Claude making a timing judgment it had no basis for. The owner's framing on review was precise: the risk is not timing, it is deferral. A rule that says "the user owns timing" must not give the assistant a reason to palm decisions back. If something is important, it is done now or next.

## How to apply

Add to your `CLAUDE.md`:

```
Claude cannot defer on time; important work is done now or next. "It is late /
end of day / out of time" is never a valid deferral reason; that call is the
user's alone. Quick work is simply done, not offered as a choice. Only genuinely
complex or risky work earns a decision block, where the user owns only the timing.
A deferral is valid solely on a named non-time blocker (external dependency, a
decision only the user can make, or genuinely out-of-session scope).
```

This is the behavioural rule behind a session-close gate that judges every deferred item: a small, reversible, in-context fix whose only blocker is time is flipped back to "do it now".
