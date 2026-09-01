---
type: Styleguide Rule
description: |-
  With strictNullChecks enabled, explicitly handle null/undefined.
  This catches null reference errors at compile time.
language: typescript
category: types
rule_id: STRICT-NULL-CHECKS
priority: error
tags:
- null-safety
- strict-mode
- correctness
---
With strictNullChecks enabled, explicitly handle null/undefined.
This catches null reference errors at compile time.

## Good

- function getName(entity: Entity | null): string { return entity?.name ?? 'unknown'; }

## Bad

- function getName(entity: Entity): string // Assumes non-null
