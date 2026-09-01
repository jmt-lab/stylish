---
type: Styleguide Rule
description: |-
  Ruff replaces flake8, isort, and more. Fast, comprehensive linting.
  Enable all relevant rule sets. Fix issues immediately.
language: python
category: practices
rule_id: RUFF-LINTING
priority: error
tags:
- ruff
- linting
- speed
---
Ruff replaces flake8, isort, and more. Fast, comprehensive linting.
Enable all relevant rule sets. Fix issues immediately.

## Good

- ruff check . --fix

## Bad

- # No linting or slow legacy tools
