# Changelog

## Unreleased

(none)

---

## v3.0 -- Stability release & public-repo polish (paired with claude-mechanisms-tools v1.0.0)

**Date:** 2026-05-10

No-content release that marks the catalog as stable. 21 mechanisms cataloged. Bundles standard public-repo artifacts that were missing — including the previously-missing LICENSE (now MIT, matching the toolkit pair).

Tracks [CC-180](https://linear.app/christophec/issue/CC-180).

### Added

- **`LICENSE`** — MIT (was missing; critical legal gap fixed)
- **`CONTRIBUTING.md`** — How to propose new mechanisms (file shape, manifest entry, cross-link expectations)
- **`CODE_OF_CONDUCT.md`** — Contributor Covenant 2.1
- **`SECURITY.md`** — Disclosure policy
- **`.github/ISSUE_TEMPLATE/bug_report.md`**, **`feature_request.md`**, **`mechanism_proposal.md`** — three issue templates including a mechanism-proposal template with explicit failure-mode + trigger + retry + structural-not-behavioral fields
- **`.github/PULL_REQUEST_TEMPLATE.md`** — PR template
- **`.gitignore`** — `.claude/`, `.DS_Store`, etc.
- **README "Stability commitment" section** — explicit v3.x guarantees: mechanism IDs permanent, file paths stable, schema preserved, cross-link contract permanent

### Changed

- **`mechanisms.yaml`** — `release_pair: v1.0.0`; comment header updated
- **GitHub repo metadata** — homepage cross-links to [`claude-mechanisms-tools`](https://github.com/christophecapel/claude-mechanisms-tools); topics added; Discussions enabled; Wiki disabled
- **`README.md`** — version badge added (v3.0), stability badge added, stability commitment section

### Stability commitment

v3.0 means existing mechanism IDs (1-21), file paths (`mechanisms/NN-name.md`), `mechanisms.yaml` schema, and the bidirectional cross-link contract with the toolkit are permanent. New mechanisms append at the next free ID; existing ones never get renumbered. See README's "Stability commitment" section.

Pairs with [`claude-mechanisms-tools` v1.0.0 release](https://github.com/christophecapel/claude-mechanisms-tools/releases/tag/v1.0.0).

---

## v2.8 -- Stale-branches digest cross-link bump (paired with claude-mechanisms-tools v0.6.0)

**Date:** 2026-05-10

### Added

- `release_pair: v0.6.0` in `mechanisms.yaml` header.
- README "Tools that implement these mechanisms" — v0.6 row added.

### Why

`claude-mechanisms-tools` v0.6.0 adds **Gate 6** to the existing `git-workflow-gate` — a SessionStart hook that scans for merged feature branches awaiting `git branch -d` cleanup. No new mechanism mapping needed: Gate 6 extends an existing tool already mapped to mechanisms #1 (Discover and derive), #11 (One branch, one scope), and #17 (Structural checks use hooks). The release-pair bump preserves bidirectional traceability between the toolkit's v0.6.0 release and the mechanisms catalog.

Pairs with [`claude-mechanisms-tools` v0.6.0 release](https://github.com/christophecapel/claude-mechanisms-tools/releases/tag/v0.6.0). Tracks [CC-179](https://linear.app/christophec/issue/CC-179).

---

## v2.7 -- Atomic Git Workflow cross-links (paired with claude-mechanisms-tools v0.5.0)

**Date:** 2026-05-09

### Added

- `implementations:` field on `mechanisms.yaml` extended:
  - **#1** (Discover and derive) — second implementation: `git-workflow-gate` (v0.5.0) alongside `/check` (v0.1.0). The gate derives branch state, rebase status, frozen-PR state, and commit-message format from the live repo before any git action — no assumption, no asking.
  - **#11** (One branch, one scope) — third implementation: `git-workflow-gate` (v0.5.0) alongside `/check` (v0.1.0) and `worktree-edit-gate` (v0.1.0). Pre-commit branch verification + frozen-branch (merged-PR) push block enforce the structural side of one-branch-one-scope.
  - **#17** (Structural checks use hooks) — fourth implementation: `git-workflow-gate` (v0.5.0) alongside `worktree-edit-gate` (v0.1.0), `plan-review-gate` (v0.2.0), and `feedback-memory-gate` (v0.4.0). Five gates as PreToolUse + PostToolUse on `Bash` matcher.
- `## Implementations` table extended on `mechanisms/01-discover-and-derive.md`, `mechanisms/11-one-branch-one-scope.md`, and `mechanisms/17-structural-checks-use-hooks.md`.
- README "Tools that implement these mechanisms" — v0.5 row added.
- `release_pair: v0.5.0` in `mechanisms.yaml` header.

### Why

`claude-mechanisms-tools` v0.5.0 ships **Atomic Git Workflow** — one tool, five gates that prevent the most common git workflow mistakes: committing to main, malformed commit messages, pushing while behind origin/main, pushing to a frozen (merged-PR) branch, and pushing without an open PR. Slim 453-LOC subset extracted from the 2,017-LOC myOS gate, decoupled from myOS-specific concerns (Linear auto-Done, session-start digest, memory-index integrity, blocked-remotes, owner-pattern). Per-repo `.commit-types` override ships verbatim.

Pairs with [`claude-mechanisms-tools` v0.5.0 release](https://github.com/christophecapel/claude-mechanisms-tools/releases/tag/v0.5.0).

---

## v2.6 -- Memory Discipline cross-links (paired with claude-mechanisms-tools v0.4.0)

**Date:** 2026-05-09

### Added

- `implementations:` field on `mechanisms.yaml` extended:
  - **#17** (Structural checks use hooks) — third implementation: `feedback-memory-gate` (v0.4.0) alongside `worktree-edit-gate` (v0.1.0) and `plan-review-gate` (v0.2.0).
  - **#5** (Deferred work needs persistent markers) — second implementation: `feedback-memory-gate` (v0.4.0) alongside `/plan-archive` (v0.2.0). The Linear ticket created in response to a bug-describing feedback memory IS the persistent marker linking the captured failure to its remediation.
- `## Implementations` table extended on `mechanisms/05-deferred-work-needs-persistent-markers.md` and `mechanisms/17-structural-checks-use-hooks.md`.
- README "Tools that implement these mechanisms" — v0.4 row added.
- `release_pair: v0.4.0` in `mechanisms.yaml` header.

### Why

`claude-mechanisms-tools` v0.4.0 ships **Memory Discipline** — a single PostToolUse hook (`feedback-memory-gate`) that nudges Claude to add a `**Linear:** CC-NN` reference whenever a feedback memory describes a bug. Soft warning, not a hard block. Battle-tested 4+ weeks before extraction. Enforces what was previously a behavioral rule — turning it into a structural check (#17) and ensuring deferred bug remediations carry persistent markers (#5).

Pairs with [`claude-mechanisms-tools` v0.4.0 release](https://github.com/christophecapel/claude-mechanisms-tools/releases/tag/v0.4.0).

---

## v2.5 -- Detection & Audit cross-links (paired with claude-mechanisms-tools v0.3.0)

**Date:** 2026-05-09

### Added

- `implementations:` field on `mechanisms.yaml` #19 and #21 extended to include `/error-audit` (v0.3.0) alongside the existing `/press1-check` (v0.1.0).
- `## Implementations` table on `mechanisms/19-detection-rules-specific-patterns.md` and `mechanisms/21-structural-intervention-beats-pattern-n-plus-1.md` extended with `/error-audit` row.
- README "Tools that implement these mechanisms" — v0.3 row added.
- `release_pair: v0.3.0` in `mechanisms.yaml` header.

### Why

`claude-mechanisms-tools` v0.3.0 ships **Detection & Audit** — `/error-audit` clusters errors across every Claude Code session transcript, surfacing top offenders by `class:tool:signature`. It complements `/press1-check` (which surfaces *expected* friction in the form of permission prompts) by surfacing *unexpected* friction in the form of recurring errors. Both implement #19 (specific patterns) and #21 (structural intervention).

Pairs with [`claude-mechanisms-tools` v0.3.0 release](https://github.com/christophecapel/claude-mechanisms-tools/releases/tag/v0.3.0).

---

## v2.4 -- Plan Discipline cross-links (paired with claude-mechanisms-tools v0.2.0)

**Date:** 2026-05-08

### Added

- `implementations:` field in `mechanisms.yaml` for mechanisms #5, #14, #16, #17 — each pointing to the corresponding v0.2.0 tool in [`claude-mechanisms-tools`](https://github.com/christophecapel/claude-mechanisms-tools).
- `## Implementations` section in `mechanisms/05-deferred-work-needs-persistent-markers.md` (new — `/plan-archive`), `mechanisms/14-trace-the-cascade.md` (new — `plan-review-gate`), `mechanisms/16-smallest-shippable-first.md` (extended), `mechanisms/17-structural-checks-use-hooks.md` (extended).
- `release_pair: v0.2.0` in `mechanisms.yaml` header.

### Why

`claude-mechanisms-tools` v0.2.0 ships **Plan Discipline** — `plan-review-gate` (Phase 1 ExitPlanMode + Phase 2 PR-create gates) and `/plan-archive` (links plan-mode files to merged PRs). Both filled previously empty `implementations:` slots. Cross-link discipline keeps the pair bidirectional: pick a tool → find the mechanism; pick a mechanism → find the tool.

Pairs with [`claude-mechanisms-tools` v0.2.0 release](https://github.com/christophecapel/claude-mechanisms-tools/releases/tag/v0.2.0).

---

## v2.3 -- Implementations cross-links + paired tools repo

**Date:** 2026-05-08

### Added

- `implementations:` field in `mechanisms.yaml` for mechanisms #1, #11, #16, #17, #19, #21. Each entry points to a tool in the new companion repo [`claude-mechanisms-tools`](https://github.com/christophecapel/claude-mechanisms-tools) (v0.1.0).
- `## Implementations` section in each affected `mechanisms/<id>-<slug>.md` linking forward to the implementing tool.
- Reciprocal cross-link table in `README.md` under "Tools that implement these mechanisms."
- `implementations_source` and `release_pair` fields in `mechanisms.yaml` header pointing at the paired tools repo and the release version.

### Why

The toolkit launch needs the cross-link to live on the mechanisms side too. Without it, the pair is one-way (tools → mechanisms) and the mechanisms catalog can't surface its own implementations. Now: pick a tool → find the mechanism. Pick a mechanism → find the tool.

The `cross_manifest_id_match` drift-gate strategy in `repo-pair-drift-gate.py` is deferred to v0.1.1 of the tools repo (per HWW #16 — smallest shippable first). v0.1 verifies cross-link integrity manually at PR review time.

---

## v2.2 -- Graduate HWW #21

**Date:** 2026-05-05

### Added

- #21 Structural intervention beats pattern N+1. The complementary stop condition to #19. After two rounds of pattern-additions on the same detector for the same failure class, the third round is architectural (change when, what, or who), not another regex. Origin: response-linter session 2026-05-04 — three rounds of reactive patterns (PRs #451, #452, #487 in myOS) before the structural fix (always-on reminder env gate flipped to default-on, PR #488) closed an in-turn lapse loop. Soft-warn Stop-hooks alone cannot close in-turn lapses; preventive injection on UserPromptSubmit was the architecture change.

### Why

#21 was promoted internally in the myOS HWW section on 2026-05-04 but never graduated to this public repo. The drift was caught the next day by `~/myOS/scripts/repo-pair-drift-gate.py`, the SessionStart-wired detector built in CC-161 specifically to surface this class of public/private drift on every session start (silent on pass per mechanism #20).

The detector that caught this is itself an instance of the pattern #21 describes: rather than adding pattern N+1 to `check-hww-parity.py` (which only covered the HWW pair), the structural fix was a registry-walker driving N strategies for N pairs. That refactor lives in myOS as `repo-pair-drift-gate.py` + `repo-pair-registry.yaml` (mechanism #15 symmetric application).

### Counts

Internal file count is the source-of-truth; the catalog enumerates in the table. With #21, the public catalog is now at 21 mechanisms. The "20+" qualitative anchor introduced in v2.1 remains the right form for marketing copy that does not need to track per-addition updates.

Closes the gap detected by `repo-pair-drift-gate.py` on 2026-05-05.

---

## Unreleased (historical, retained for context)

### Changed

- Mechanism #13 title aligned to myOS HWW source of truth. H1 and README link text updated from "Dry-run before data-patching [scripts]" to "Dry-run before committing data-patching scripts" (the word "committing" is a substantive qualifier, the dry-run happens before the first commit of the script, not every run). Filename kept unchanged (`mechanisms/13-dry-run-before-data-patching.md`) to preserve URL stability. `mechanisms.yaml` entry also updated. Detected by `~/myOS/scripts/check-hww-parity.py` phase 2 title-match check (CC-104).

---

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
