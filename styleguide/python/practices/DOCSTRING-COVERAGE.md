---
type: Styleguide Rule
description: |-
  Use interrogate or pydocstyle to enforce docstrings on public APIs.
  Documentation is part of code quality.
language: python
category: practices
rule_id: DOCSTRING-COVERAGE
priority: info
tags:
- docstrings
- documentation
- quality
---
Use interrogate or pydocstyle to enforce docstrings on public APIs.
Documentation is part of code quality.

## Good

- interrogate -v src/ --fail-under=80

## Bad

- # No docstring enforcement
