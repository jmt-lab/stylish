---
type: Styleguide Rule
description: |-
  Install pre-commit framework. Run ruff, mypy, tests before commit.
  Catch issues before they reach CI.
language: python
category: practices
rule_id: PRE-COMMIT-HOOKS
priority: error
tags:
- pre-commit
- automation
- prevention
---
Install pre-commit framework. Run ruff, mypy, tests before commit.
Catch issues before they reach CI.

## Good

- # .pre-commit-config.yaml with ruff, mypy
pre-commit install

## Bad

- # No pre-commit checks
# Issues found in CI
