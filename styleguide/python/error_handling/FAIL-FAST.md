---
type: Styleguide Rule
description: |-
  For programmer errors (invalid state, broken invariants), fail
  immediately with assertion or exception. Don't try to recover.
language: python
category: error_handling
rule_id: FAIL-FAST
priority: error
tags:
- correctness
- debugging
- safety
---
For programmer errors (invalid state, broken invariants), fail
immediately with assertion or exception. Don't try to recover.

## Good

- assert state in VALID_STATES, f'Invalid state: {state}'
- if not self._initialized:
    raise RuntimeError('Must call initialize() first')

## Bad

- if state not in VALID_STATES:
    state = DEFAULT_STATE  # Hiding bug
