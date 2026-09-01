---
type: Styleguide Rule
description: |-
  Single-letter type parameters (T, U, V) are fine for generic utilities.
  Use descriptive names when the parameter has specific meaning.
language: rust
category: naming
rule_id: TYPE-PARAMETERS-DESCRIPTIVE
priority: info
tags:
- naming
- generics
- clarity
- carmack
---
Single-letter type parameters (T, U, V) are fine for generic utilities.
Use descriptive names when the parameter has specific meaning.

## Good

- struct Array<T> {} // Generic, T is fine
- struct EntityManager<Entity, Component> {} // Specific, descriptive
- fn transform<Input, Output>(data: Input) -> Output

## Bad

- struct EntityManager<T, U> {} // Too generic for specific types
