---
type: Styleguide Rule
description: |-
  Keep related types, functions, and classes together in the same file
  or directory. Don't scatter related code across the codebase.
language: typescript
category: organization
rule_id: RELATED-CODE-TOGETHER
priority: info
tags:
- organization
- cohesion
- readability
---
Keep related types, functions, and classes together in the same file
or directory. Don't scatter related code across the codebase.

## Good

- // user.ts
export interface User { }
export function createUser(): User { }
export function validateUser(u: User): boolean { }

## Bad

- // types/user.ts, factories/user.ts, validators/user.ts - scattered
