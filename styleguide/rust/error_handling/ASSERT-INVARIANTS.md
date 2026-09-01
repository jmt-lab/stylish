---
type: Styleguide Rule
description: |-
  Carmack principle: Assert invariants everywhere. Use assert! for
  conditions that must hold. Panics in debug, optimized out in release.
language: rust
category: error_handling
rule_id: ASSERT-INVARIANTS
priority: error
tags:
- errors
- assertions
- invariants
- carmack
---
Carmack principle: Assert invariants everywhere. Use assert! for
conditions that must hold. Panics in debug, optimized out in release.

## Good

- assert!(position.x.is_finite());
- assert!(health >= 0.0 && health <= max_health);
- assert!(!entities.is_empty(), "Must have at least one entity");

## Bad

- // Missing assertion
if health < 0.0 { health = 0.0; } // Hiding bug
