---
type: Styleguide Rule
description: |-
  Exception messages should include relevant context (values, state) to
  aid debugging. Make errors actionable.
language: python
category: error_handling
rule_id: EXCEPTION-MESSAGES
priority: warn
tags:
- exceptions
- debugging
- clarity
---
Exception messages should include relevant context (values, state) to
aid debugging. Make errors actionable.

## Good

- raise ValueError(f'Invalid size {size}, must be 0-{MAX_SIZE}')
- raise FileNotFoundError(f'Config not found: {path}')

## Bad

- raise ValueError('Invalid size')  # What size? What's valid?
