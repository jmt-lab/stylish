---
type: Styleguide Rule
description: |-
  Ruff handles import sorting (replaces isort). Group stdlib,
  third-party, and local imports. Automate in pre-commit.
language: python
category: practices
rule_id: IMPORT-SORTING
priority: warn
tags:
- imports
- formatting
- consistency
---
Ruff handles import sorting (replaces isort). Group stdlib,
third-party, and local imports. Automate in pre-commit.

## Good

- # ruff check --select I --fix

## Bad

- # Random import order
