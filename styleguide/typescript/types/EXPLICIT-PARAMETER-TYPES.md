---
type: Styleguide Rule
description: |-
  Always specify types for function parameters. Don't rely on inference
  for inputs - make the contract explicit.
language: typescript
category: types
rule_id: EXPLICIT-PARAMETER-TYPES
priority: error
tags:
- parameters
- contracts
- clarity
---
Always specify types for function parameters. Don't rely on inference
for inputs - make the contract explicit.

## Good

- function process(entity: Entity, count: number): void

## Bad

- function process(entity, count) // Implicit any
