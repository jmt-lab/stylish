---
type: Styleguide Rule
description: |-
  Use Prettier for all formatting. Don't bikeshed formatting in code review.
  Run on save and in pre-commit hooks. Frees code review for logic.
language: typescript
category: formatting
rule_id: TS-FMT-PRETTIER
priority: error
tags:
- tooling
- automation
- prettier
- formatting
---
Use Prettier for all formatting. Don't bikeshed formatting in code review.
Run on save and in pre-commit hooks. Frees code review for logic.

## Good

- // .prettierrc configured and enforced in CI
- npm run format -- checks Prettier compliance
- // Pre-commit hook runs prettier

## Bad

- // Manual formatting without Prettier
- // Debating brace placement in code review
- // Inconsistent style across files
