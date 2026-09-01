---
type: Styleguide Rule
description: |-
  Always use "strict": true in tsconfig.json. This enables all strict type
  checking options including strictNullChecks, noImplicitAny, and more.
  Catches null/undefined bugs, implicit any, and type errors at compile time.
  Aligns with Carmack's static analysis mandate.
language: typescript
category: types
rule_id: STRICT-MODE-MANDATORY
priority: error
tags:
- configuration
- static-analysis
- safety
- typescript
- compiler
---
Always use "strict": true in tsconfig.json. This enables all strict type
checking options including strictNullChecks, noImplicitAny, and more.
Catches null/undefined bugs, implicit any, and type errors at compile time.
Aligns with Carmack's static analysis mandate.

## Good

- {"compilerOptions": {"strict": true}}

## Bad

- {"compilerOptions": {"strict": false}}
