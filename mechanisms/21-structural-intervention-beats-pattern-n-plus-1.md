# Structural intervention beats pattern N+1

> When a detector has accumulated multiple specific patterns and the same class of failure keeps recurring, the next move is structural, not another pattern.

## The mechanism

When a detection mechanism (linter, gate, hook, validator) has caught a class of failure several times and the failure still recurs, adding pattern N+1 is the wrong move. The right move is structural: change the *when* (preventive arm before the lapse, not reactive reminder after), the *what* (hard block before the action, not warn after), or the *who* (different enforcement layer entirely).

Mechanism #19 covers the single-miss path: a detector misses a real failure, so add the specific pattern and capture the literal failure string. #21 is the complementary stop condition. After several rounds of pattern-additions to the same surface, the N+1 pattern always exists, but the architecture change is what actually changes the regime.

The rule:

- **First or second miss:** apply #19. Add the specific pattern, capture the literal failure string as a regression test fixture.
- **Third miss on the same surface:** stop adding patterns. Step back and change the architecture: when, what, or who.
- **Soft-warn Stop-hooks alone cannot close in-turn lapses.** They fire after the response streams. If the failure mode is in-turn behavior, the enforcement layer needs to fire before the response is generated, not after.

## Why this exists

The response-linter session on 2026-05-04 measured three rounds of reactive pattern-additions on the same surface before the structural fix landed:

- PR #451 added per-pattern cap and two new patterns
- PR #452 added a rephrasing pattern
- PR #487 added an if-you pattern
- The same in-turn lapse kept recurring across sessions despite each new regex

Only PR #488 closed the lapse loop, by flipping the always-on HWW reminder from opt-in to opt-out (default-on env gate). The fix was not pattern N+1. It was preventive injection on every turn, before the model generated the response that would have lapsed.

The recurrence pattern is the signal. If the same failure shape returns after pattern N has been added, the regex layer has hit its ceiling. The next gain comes from a different layer.

## How to apply

Add to your `CLAUDE.md`:

```
Structural intervention beats pattern N+1. After two rounds of adding specific patterns
to the same detector for the same failure class, the next round is architectural,
not another regex. Change when, what, or who, not how many.
```

Trigger: when reviewing a detector that has grown a third pattern for the same failure surface, or when the same in-turn behavior keeps lapsing across sessions despite new regexes shipping.

Decision tree at the third miss:

1. **Is the failure in-turn behavior?** Reactive Stop-hooks cannot close it. Move the enforcement to a preventive layer (UserPromptSubmit injection, system prompt addition, or environment-gated reminder).
2. **Is the failure a structural condition** (file present, section in diff, keyword in commit)? Move from soft warn to hard block.
3. **Is the failure spanning multiple surfaces?** The detector layer is wrong. Move to a higher abstraction (PreToolUse on the broader event, not PostToolUse on the narrow one).

Pair with mechanism #19. They are complementary: #19 prevents complacency at miss 1; #21 prevents accumulation at miss 3.
