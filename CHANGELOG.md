# Changelog

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
