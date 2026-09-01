---
type: Styleguide Rule
description: |-
  CI must run mypy, ruff, tests, coverage. Block merges on failures.
  Static analysis is mandatory, not optional.
language: python
category: practices
rule_id: CI-STATIC-ANALYSIS
priority: error
tags:
- ci
- automation
- enforcement
---
CI must run mypy, ruff, tests, coverage. Block merges on failures.
Static analysis is mandatory, not optional.

## Good

- # CI: mypy, ruff, pytest, coverage
# PR blocked on failure

## Bad

- # Manual checks only
