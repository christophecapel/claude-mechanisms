# Structural checks use hooks, not behavioral rules

> If a check is structural (section present, file in diff, keyword exists), enforce it with a hook. Behavioral rules fail under cognitive load.

## The mechanism

If a check is structural, enforce it with a hook. Not a memory, not a rule in `CLAUDE.md`, not a note in the PR template. A structural check is anything answerable by inspecting the artifact itself:

- A required section is present
- A specific file is staged
- A keyword appears in the diff
- A count matches an expected value
- A pattern validates against a regex

These are objective, machine-checkable facts. They do not require judgment. Every time you rely on "remember to check X" instead of "the hook asserts X," you accept a failure rate proportional to cognitive load.

Reserve behavioral rules for the opposite case: semantic checks that require judgment. "Is this tone appropriate for the audience?" "Does this claim match the receipts?" Those cannot be hooked.

## Why this exists

Two memory mechanisms told Claude to cross-check plans before `ExitPlanMode`. The planning session still missed thirteen gaps. Not because the memories were wrong, they triggered. Because cross-checking is cognitive work, and cognitive work degrades under scope load. By the time the plan was ready to exit, the rule had been applied at reduced fidelity.

The fix was not a stronger rule. It was a hook: `plan-review-gate.py`, which reads the plan file and asserts the presence of specific sections before allowing `ExitPlanMode` to complete. No remembering required. Deterministic. Either the section is there or the tool call fails with a structured error.

Two incidents in one day (2026-04-13) was the forcing function. Promoted to HWW the same day.

## How to apply

Add to your `CLAUDE.md`:

```
Structural checks use hooks, not behavioral rules. If a check is structural (section present, file in diff, keyword exists), enforce it with a hook. Behavioral rules fail under cognitive load. Reserve rules for semantic checks that require judgment.
```

Trigger: any time you catch yourself writing "remember to X" or "always check Y" in a memory file, rule, or `CLAUDE.md` instruction. Before shipping it as a rule, ask: "Is X structural?" If yes, write a hook instead.
