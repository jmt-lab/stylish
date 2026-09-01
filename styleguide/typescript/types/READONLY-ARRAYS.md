---
type: Styleguide Rule
description: |-
  Mark array parameters as readonly when they won't be modified. This
  prevents accidental mutation and documents intent.
language: typescript
category: types
rule_id: READONLY-ARRAYS
priority: error
tags:
- arrays
- immutability
- const-discipline
---
Mark array parameters as readonly when they won't be modified. This
prevents accidental mutation and documents intent.

## Good

- function sum(numbers: readonly number[]): number

## Bad

- function sum(numbers: number[]): number // Might mutate
