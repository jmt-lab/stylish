---
type: Styleguide Rule
description: |-
  ESLint is TypeScript's static analyzer. Use @typescript-eslint plugin.
  It is irresponsible not to use it. Run continuously, not occasionally.
language: typescript
category: practices
rule_id: ESLINT-MANDATORY
priority: error
tags:
- eslint
- static-analysis
- mandatory
---
ESLint is TypeScript's static analyzer. Use @typescript-eslint plugin.
It is irresponsible not to use it. Run continuously, not occasionally.

## Good

- // .eslintrc.js with @typescript-eslint/recommended
- // CI runs: eslint --max-warnings 0

## Bad

- // No ESLint configuration
- // ESLint warnings ignored
