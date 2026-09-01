---
type: Styleguide Rule
description: |-
  Structure conditionals so the common case is first. Modern CPUs
  predict branches; help them predict correctly.
language: rust
category: optimization
rule_id: BRANCH-PREDICTION
priority: info
tags:
- optimization
- branches
- cpu
---
Structure conditionals so the common case is first. Modern CPUs
predict branches; help them predict correctly.

## Good

- if likely_condition {
    // Common hot path
} else {
    // Rare cold path
}

## Bad

- if rare_error {
    // Rare branch first
} else {
    // Common path nested
}
