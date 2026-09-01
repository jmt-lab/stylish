---
type: Styleguide Rule
description: |-
  All tools should report zero warnings. Fix new warnings immediately.
  Warnings hide real problems.
language: python
category: practices
rule_id: ZERO-WARNINGS-POLICY
priority: error
tags:
- warnings
- discipline
- hygiene
---
All tools should report zero warnings. Fix new warnings immediately.
Warnings hide real problems.

## Good

- # mypy: 0 errors
# ruff: 0 issues

## Bad

- # 127 mypy errors (what's 1 more?)
