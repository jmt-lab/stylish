---
type: Styleguide Rule
description: |-
  Track percentage of typed code. Aim for 100% in new code.
  Use mypy --strict and monitor coverage metrics.
language: python
category: practices
rule_id: TYPE-COVERAGE
priority: warn
tags:
- types
- coverage
- metrics
---
Track percentage of typed code. Aim for 100% in new code.
Use mypy --strict and monitor coverage metrics.

## Good

- # mypy coverage: 98%
# All new code typed

## Bad

- # mypy coverage: 45%
# Many Any types
