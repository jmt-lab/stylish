---
type: Styleguide Rule
description: |-
  Use husky or similar to run linting and formatting before commit.
  Catch issues before they reach CI. Run lint-staged for speed.
language: typescript
category: practices
rule_id: PRE-COMMIT-HOOKS
priority: warn
tags:
- git-hooks
- automation
- prevention
---
Use husky or similar to run linting and formatting before commit.
Catch issues before they reach CI. Run lint-staged for speed.

## Good

- // husky + lint-staged: lint and format changed files

## Bad

- // No pre-commit validation
