---
type: Styleguide Rule
description: |-
  Enable noImplicitAny in tsconfig. Every value should have an explicit
  or properly inferred type - no silent 'any' fallbacks.
language: typescript
category: types
rule_id: NO-IMPLICIT-ANY
priority: error
tags:
- configuration
- safety
- strict-mode
---
Enable noImplicitAny in tsconfig. Every value should have an explicit
or properly inferred type - no silent 'any' fallbacks.

## Good

- {"compilerOptions": {"noImplicitAny": true}}

## Bad

- {"compilerOptions": {"noImplicitAny": false}}
