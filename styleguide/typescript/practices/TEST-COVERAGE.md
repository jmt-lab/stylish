---
type: Styleguide Rule
description: |-
  Track test coverage. Set minimum thresholds. Focus on critical
  paths and complex logic, not arbitrary percentage targets.
language: typescript
category: practices
rule_id: TEST-COVERAGE
priority: warn
tags:
- testing
- coverage
- quality
---
Track test coverage. Set minimum thresholds. Focus on critical
paths and complex logic, not arbitrary percentage targets.

## Good

- // jest --coverage --coverageThreshold=80

## Bad

- // No coverage tracking
