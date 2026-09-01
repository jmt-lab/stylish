---
type: Styleguide Rule
description: |-
  Use tox or CI matrix to test against supported Python versions.
  Catch version-specific issues early.
language: python
category: practices
rule_id: MULTIPLE-PYTHON-VERSIONS
priority: warn
tags:
- compatibility
- testing
- versions
---
Use tox or CI matrix to test against supported Python versions.
Catch version-specific issues early.

## Good

- # CI matrix: [3.9, 3.10, 3.11, 3.12]

## Bad

- # Only test on developer's Python version
