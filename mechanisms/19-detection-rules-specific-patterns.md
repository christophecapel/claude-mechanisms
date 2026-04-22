# Detection rules: more specific patterns, never broader allowlists

> When a detector misses a real failure, the fix is always more specific patterns, never "better judgment" or broader suppression.

## The mechanism

When a detection mechanism (a linter, a gate, a hook, a regex-based check) misses a real failure, the fix is structural. Tighten the pattern. Add the exact failure string. Write a regression test that fails without the fix and passes with it. Never: "add a note telling the agent to try harder." Never: "broaden the allowlist so this kind of thing stops tripping." Never: "rely on better judgment next time."

Two failure modes to avoid:

- **Bare-noun allowlists leak.** If you allowlist a word, every sentence containing that word passes. Context-free matching is almost always too permissive.
- **Broad matchers miss variants.** If the pattern is abstract, small textual variations break detection entirely.

The only reliable path is the specific one: observe the miss in the wild, add the exact pattern (phrase, token, structure), add a regression test using the exact failure string. Detection ratchets tighter over time, never looser.

## Why this exists

Three incidents in one week (2026-04-15 to 2026-04-16) on the response-linter: post-approval stalling, pick-your-starting-task leakage, and a noun-trap allowlist leak. Each time, the first instinct was to broaden: relax the matcher, widen the allowlist, trust the model to "know" when the rule applies.

Each broadening opened a new leak path. The pattern that finally held was the opposite: every miss got a named regression case with the exact triggering text, and the detector grew a more specific pattern to catch it. Detection coverage tightened, false-positive rate stayed flat, and the same class of failure stopped recurring.

Promoted 2026-04-16 after the third incident in a single week.

## How to apply

Add to your `CLAUDE.md`:

```
Detection rules: more specific patterns, never broader allowlists. When a linter/gate/hook misses a real failure, fix by tightening: add the exact pattern, add a regression test using the exact failure string. Never broaden allowlists or rely on "better judgment."
```

Trigger: any time a detection mechanism fails to flag a real problem. When the trigger fires, do not relax the matcher. Capture the exact failure string, add it as a regression test, add a specific pattern that catches it.
