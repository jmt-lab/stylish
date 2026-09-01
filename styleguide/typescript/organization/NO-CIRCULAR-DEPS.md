---
type: Styleguide Rule
description: |-
  Circular dependencies indicate poor separation of concerns and cause
  initialization issues. Refactor to introduce a third module or interface.
language: typescript
category: organization
rule_id: NO-CIRCULAR-DEPS
priority: error
tags:
- dependencies
- architecture
- modularity
---
Circular dependencies indicate poor separation of concerns and cause
initialization issues. Refactor to introduce a third module or interface.

## Good

- // types.ts
export interface IUser { }
// user.ts imports types
// product.ts imports types

## Bad

- // user.ts imports product.ts
// product.ts imports user.ts
