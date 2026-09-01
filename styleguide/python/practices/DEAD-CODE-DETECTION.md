---
type: Styleguide Rule
description: |-
  Use vulture or ruff to find unused code. Dead code is a maintenance
  burden and hides bugs. Remove it.
language: python
category: practices
rule_id: DEAD-CODE-DETECTION
priority: warn
tags:
- dead-code
- maintenance
- cleanup
---
Use vulture or ruff to find unused code. Dead code is a maintenance
burden and hides bugs. Remove it.

## Good

- vulture src/ --min-confidence 80

## Bad

- # Thousands of lines of unused code
