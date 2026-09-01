---
type: Styleguide Rule
description: |-
  Add constraints to generic type parameters to document requirements
  and enable type-safe operations.
language: typescript
category: types
rule_id: GENERIC-CONSTRAINTS
priority: warn
tags:
- generics
- constraints
- safety
---
Add constraints to generic type parameters to document requirements
and enable type-safe operations.

## Good

- function getId<T extends { id: number }>(entity: T): number

## Bad

- function getId<T>(entity: T): number // Unconstrained
