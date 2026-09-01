---
type: Styleguide Rule
description: |-
  Use const for all bindings unless reassignment is required. This makes
  mutation explicit and prevents accidental reassignment bugs.
language: typescript
category: functional
rule_id: CONST-BY-DEFAULT
priority: error
tags:
- immutability
- const
- bindings
---
Use const for all bindings unless reassignment is required. This makes
mutation explicit and prevents accidental reassignment bugs.

## Good

- const result = transform(input);
- const items = [1, 2, 3];

## Bad

- let result = transform(input); // Never reassigned
- var items = [1, 2, 3]; // Never use var
