---
type: Styleguide Rule
description: |-
  Codebase must have zero warnings. Fix immediately. Don't let warnings
  accumulate - they hide real problems.
language: typescript
category: practices
rule_id: ZERO-WARNINGS-POLICY
priority: error
tags:
- warnings
- discipline
- hygiene
---
Codebase must have zero warnings. Fix immediately. Don't let warnings
accumulate - they hide real problems.

## Good

- // eslint --max-warnings 0 in CI

## Bad

- // 247 warnings (what's one more?)
