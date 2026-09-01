---
type: Styleguide Rule
description: |-
  Model state with discriminated unions. This makes all possible states
  explicit and enables exhaustive checking.
language: typescript
category: types
rule_id: DISCRIMINATED-UNIONS
priority: error
tags:
- state
- unions
- correctness
---
Model state with discriminated unions. This makes all possible states
explicit and enables exhaustive checking.

## Good

- type Result<T> = { status: 'success'; data: T } | { status: 'error'; error: Error }

## Bad

- type Result<T> = { data?: T; error?: Error } // Ambiguous state
