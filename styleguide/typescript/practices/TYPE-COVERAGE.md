---
type: Styleguide Rule
description: |-
  Use type-coverage tool to measure percentage of typed code.
  Aim for 100%. Any is a hole in type safety.
language: typescript
category: practices
rule_id: TYPE-COVERAGE
priority: warn
tags:
- types
- coverage
- metrics
---
Use type-coverage tool to measure percentage of typed code.
Aim for 100%. Any is a hole in type safety.

## Good

- // type-coverage --at-least 95

## Bad

- // Unknown type coverage, any everywhere
