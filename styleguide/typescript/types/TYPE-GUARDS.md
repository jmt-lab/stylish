---
type: Styleguide Rule
description: |-
  Create type guard functions to narrow unknown or union types. Type guard
  functions should return 'value is Type' predicates to enable proper type
  narrowing in calling code. This makes narrowing explicit and reusable.
language: typescript
category: types
rule_id: TYPE-GUARDS
priority: warn
tags:
- type-guards
- narrowing
- reusability
- predicates
---
Create type guard functions to narrow unknown or union types. Type guard
functions should return 'value is Type' predicates to enable proper type
narrowing in calling code. This makes narrowing explicit and reusable.

## Good

- function isEntity(value: unknown): value is Entity { return typeof value === 'object' && value !== null && 'id' in value; }
- function isString(value: unknown): value is string

## Bad

- if (typeof value === 'object' && 'id' in value) // Repeated logic
- function isString(value: unknown): boolean // Missing type predicate
