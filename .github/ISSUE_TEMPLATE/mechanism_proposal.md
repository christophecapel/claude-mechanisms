---
name: Propose a new mechanism
about: A new operating mechanism for the catalog
title: "[mechanism] "
labels: mechanism-proposal
---

## Failure mode

<!-- What real failure does this mechanism prevent? Specific incidents are stronger than abstract reasoning. When did it happen? How often does it recur? -->

## Trigger

<!-- When does the mechanism fire? Manual? Automatic via hook/gate? Lifecycle event? "Whenever I X" without a structural trigger means it'll fail under cognitive load. -->

## Retry logic

<!-- What happens if the trigger fires but the outcome isn't met? How many attempts? Backoff? -->

## Failure path

<!-- What happens when retries are exhausted? Notification? Escalation? Never fail silently. -->

## Why this is structural, not behavioral

<!-- Behavioral rules ("remember to X") fail under cognitive load. Structural mechanisms have automatic triggers. Make the case that this is the latter. -->

## Proposed file

<!-- Suggest the mechanism's slot: which ID number? What's the short title? -->

## Implementation candidate

<!-- Is there a tool in claude-mechanisms-tools that should pair with this? Or one that should be built? Link or describe. -->

## Evidence

<!-- Where has this been battle-tested? What's the duration / incident count that justifies adding it to the catalog? -->
