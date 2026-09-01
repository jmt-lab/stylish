---
type: Styleguide Rule
description: |-
  CI must run ESLint, TypeScript compiler, and tests. Block merges
  that introduce warnings or type errors.
language: typescript
category: practices
rule_id: CI-STATIC-ANALYSIS
priority: error
tags:
- ci
- automation
- enforcement
---
CI must run ESLint, TypeScript compiler, and tests. Block merges
that introduce warnings or type errors.

## Good

- // CI: tsc --noEmit && eslint . --max-warnings 0

## Bad

- // No automated checks in CI
