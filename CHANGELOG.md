# Changelog

## v2.1 -- Graduate HWW #17-20; drop count anchors

**Date:** 2026-04-22

### Added

- #17 Structural checks use hooks, not behavioral rules (origin: `plan-review-gate`, 2026-04-13, two incidents in one day)
- #18 Safest path first on destructive ops (origin: 2026-04-15 near-miss on public-fork delete)
- #19 Detection rules: more specific patterns, never broader allowlists (origin: response-linter sessions 2026-04-15 to 2026-04-16, three incidents in one week)
- #20 Hooks silent on pass (origin: hook-efficiency session 2026-04-21, measured across 30 sessions)

### Changed

- Removed numeric mechanism-count from README badge, prose, and the "The N mechanisms" section heading. Count claims in public artifacts created a recurring sync burden with every addition. Internal file count remains the source-of-truth; the catalog is enumerated in the table. At 20+ mechanisms, a "20+" qualitative anchor may be used for weight without requiring per-addition updates.
- Removed count references from the repo `CLAUDE.md` (`16 operating mechanisms` -> `operating mechanisms`; `numbered 01-16` -> `numbered sequentially`).

### Why

Four mechanisms had been promoted internally in the myOS HWW section but never graduated to this public repo. This was a Tier-1 failure class: a behavioral rule ("remember to sync") that failed under cognitive load. A Linear ticket (CC-101) was filed 2026-04-21 to close the gap. A follow-up ticket covers a structural gate (manifest + parity check) so the same class of drift cannot recur.

Closes CC-101.

---

## v2.0 -- 16 Mechanisms (consolidated)

**Date:** 2026-04-10

Consolidated from 20 internal principles to 16 public mechanisms. Merged overlapping principles, added 4 new mechanisms from production use.

### Changes

**Merged:**
- #01 (Read before creating) + #05 (Auto-derive) + #14 (Discover, don't compute) -> #01 Discover and derive, never assume or ask
- #12 (One PR, one scope) + #13 (Branch = scope boundary) -> #11 One branch, one scope

**Added:**
- #13 Dry-run before data-patching scripts
- #14 Trace the cascade before exiting plan mode
- #15 Build callables, not embedded logic
- #16 Smallest shippable first

**Renumbered:** #06-#11 shifted down to #05-#10, #15 became #12

### Why

5 overlap clusters were discovered across 20 principles + 50 feedback memories. Three principles (old #1, #5, #14) all encoded "look before you leap" at different zoom levels. Two principles (old #12, #13) both addressed branch/scope discipline. Consolidation reduced total rule count by 21 items with zero signal loss.

---

## v1.0 -- 15 Mechanisms

**Date:** 2026-04-09

Initial release. 15 mechanisms for Claude Code, shipped alongside LinkedIn post #1.
