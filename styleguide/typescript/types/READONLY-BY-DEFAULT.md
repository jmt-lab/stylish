---
type: Styleguide Rule
description: |-
  Properties should be readonly unless there's a specific reason for
  mutability. This is TypeScript's equivalent of const correctness.
  Mark arrays and object properties readonly when they shouldn't change —
  TypeScript enforces immutability at compile time.
language: typescript
category: types
rule_id: READONLY-BY-DEFAULT
priority: error
tags:
- immutability
- const-discipline
- safety
- readonly
- types
---
Properties should be readonly unless there's a specific reason for
mutability. This is TypeScript's equivalent of const correctness.
Mark arrays and object properties readonly when they shouldn't change —
TypeScript enforces immutability at compile time.

## Good

- interface Entity { readonly id: number; readonly name: string; }
- function process(data: readonly number[]): void
- interface Config { readonly apiUrl: string; }
- function process(items: readonly number[]): number

## Bad

- interface Entity { id: number; name: string; } // Never modified
- function process(items: number[]): number // Might mutate
- interface Config { apiUrl: string; } // Mutable
