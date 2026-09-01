---
type: Styleguide Rule
description: |-
  Public functions and methods must have explicit return types. This
  documents the contract and prevents accidental type changes.
language: typescript
category: types
rule_id: EXPLICIT-RETURN-TYPES
priority: error
tags:
- api
- documentation
- contracts
---
Public functions and methods must have explicit return types. This
documents the contract and prevents accidental type changes.

## Good

- export function getEntity(id: number): Entity | null
- public getName(): string

## Bad

- export function getEntity(id: number) // Inferred return type
