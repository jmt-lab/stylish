---
type: Styleguide Rule
description: |-
  Files should focus on a single class, interface, or cohesive set of related
  functions. Avoid mixing unrelated exports in one file.
language: typescript
category: organization
rule_id: ONE-MODULE-PER-FILE
priority: warn
tags:
- modules
- organization
- cohesion
---
Files should focus on a single class, interface, or cohesive set of related
functions. Avoid mixing unrelated exports in one file.

## Good

- // user.ts
export class User { }
- // validation.ts
export function validate() { }
export function sanitize() { }

## Bad

- // utils.ts
export class User { }
export class Product { }
export function parseDate() { }
