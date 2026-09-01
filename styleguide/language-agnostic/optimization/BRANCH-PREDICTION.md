---
type: Styleguide Rule
description: |-
  Structure conditionals to favor the common path. Modern CPUs predict
  branches; help them predict correctly. Consistent execution is fast.
language: language-agnostic
category: optimization
rule_id: BRANCH-PREDICTION
priority: info
tags:
- branches
- cpu
- prediction
---
Structure conditionals to favor the common path. Modern CPUs predict
branches; help them predict correctly. Consistent execution is fast.

## Good

- if (likely_condition) { /* common path */ }

## Bad

- if (rare_error) { /* rare branch */ } else { /* common path */ }
