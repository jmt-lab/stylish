---
type: Styleguide Rule
description: |-
  Use pytest-cov to measure coverage. Set minimum thresholds.
  Focus on critical paths, not 100% coverage.
language: python
category: practices
rule_id: COVERAGE-TRACKING
priority: warn
tags:
- coverage
- testing
- metrics
---
Use pytest-cov to measure coverage. Set minimum thresholds.
Focus on critical paths, not 100% coverage.

## Good

- pytest --cov=src --cov-report=term --cov-fail-under=80

## Bad

- # No coverage tracking
