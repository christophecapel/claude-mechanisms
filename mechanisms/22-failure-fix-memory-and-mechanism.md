# A failure fix is a memory AND a mechanism

> When fixing a failure, logging a note is not enough — pair it with enforcement. A memory records what went wrong; a mechanism prevents it from recurring. A memory-only fix to a failure is incomplete.

## The mechanism

When you fix a *failure* — a bug, a mistake, a recurring lapse, anything that "shouldn't happen again" — the fix has two halves:

- **The memory** — a note capturing what happened and why (a feedback memory, a ticket, a changelog entry, a doc). This is recall, not prevention.
- **The mechanism** — enforcement that catches or prevents the failure automatically next time: a hook, a gate, a linter rule, a test, a script, a workflow check.

A memory alone relies on a human (or an agent) remembering to apply it under load — which is exactly the condition that produced the failure. Enforcement does not forget. So: every failure fix names a mechanism, not just a memory.

Carve-outs — a memory (or nothing) is fine when:

- The work is a **new feature** or a one-off decision, not a failure being prevented from recurring.
- A **pure code fix carries its own regression test** — the test *is* the mechanism.
- The mechanism is explicitly tracked as a **separate, sequenced next step** with a concrete reason it cannot ship in the same change (genuine sequencing, not a vague "later").

## Why this exists

After a large multi-part epic shipped "complete" — every child unit-tested, a structural review-gate green — a single end-to-end dry-run immediately surfaced three real gaps the tests and the gate had all passed over. The owner's reaction crystallized the rule: "a memory alone is an unacceptable resolution to a failure; any fix relying on just a feedback memory should be rejected."

Capturing that lesson as *only a memory* would have been self-contradictory. So it shipped as both a written principle **and** its own enforcement: a semantic-judge class in the response linter that flags a response resolving a failure with a memory/ticket and no named mechanism. The principle enforces itself.

## How to apply

Add to your `CLAUDE.md`:

```
A failure fix is a memory AND a mechanism. Fixing a failure (bug, mistake, recurring
lapse) with only a note — a memory, a ticket — is incomplete. Pair it with enforcement
(hook, gate, linter rule, test, script) that prevents recurrence. Carve-outs: new features,
one-off decisions, a code fix with its own regression test, or a mechanism explicitly
tracked as a sequenced next step.
```

Trigger: any time you catch yourself writing "I've noted this so it won't happen again" or "filed a ticket / saved a memory" as the resolution to a *failure*. Ask: what enforces this next time? If the answer is "I'll remember," it is not yet fixed. Enforcement can be warn-class (a soft nudge that fires after the fact) when an in-the-moment block is architecturally impossible — but there must be a mechanism, not just a note.
