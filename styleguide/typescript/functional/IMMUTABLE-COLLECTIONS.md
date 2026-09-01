---
type: Styleguide Rule
description: |-
  For function parameters and return types, prefer readonly collections
  to signal immutability and prevent accidental mutation.
language: typescript
category: functional
rule_id: IMMUTABLE-COLLECTIONS
priority: warn
tags:
- readonly
- collections
- immutability
---
For function parameters and return types, prefer readonly collections
to signal immutability and prevent accidental mutation.

## Good

- function sum(nums: ReadonlyArray<number>): number
- function getIds(items: ReadonlySet<Item>): string[]

## Bad

- function sum(nums: number[]): number // Might mutate
- function getIds(items: Set<Item>): string[]
