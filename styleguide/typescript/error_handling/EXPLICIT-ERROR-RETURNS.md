---
type: Styleguide Rule
description: |-
  Functions that can fail should make this obvious in return type. Use
  Result, Option, or nullable types, never implicit undefined.
language: typescript
category: error_handling
rule_id: EXPLICIT-ERROR-RETURNS
priority: error
tags:
- type-safety
- explicit-errors
- contracts
---
Functions that can fail should make this obvious in return type. Use
Result, Option, or nullable types, never implicit undefined.

## Good

- function findEntity(id: number): Entity | null { ... }
- function loadData(): Result<Data, LoadError> { ... }
- function tryParse(s: string): number | undefined { ... }

## Bad

- function findEntity(id: number): Entity { ... } // What if not found?
