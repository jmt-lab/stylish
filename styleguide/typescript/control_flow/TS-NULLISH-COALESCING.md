---
type: Styleguide Rule
description: |-
  Use nullish coalescing (??) instead of || when you only want to
  handle null/undefined, not falsy values like 0 or ''.
language: typescript
category: control_flow
rule_id: TS-NULLISH-COALESCING
priority: warn
tags:
- nullish
- defaults
- operators
---
Use nullish coalescing (??) instead of || when you only want to
handle null/undefined, not falsy values like 0 or ''.

## Good

- const count = input ?? 0; // Only null/undefined

## Bad

- const count = input || 0; // Also replaces 0 with 0
