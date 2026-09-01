---
type: Styleguide Rule
description: |-
  Use assert for internal invariants (programmer errors). Use raise for
  validation errors (user/external errors). Asserts can be disabled.
  Preconditions on function parameters from external/user input =
  validation (use raise). Preconditions on internal state that should
  be impossible to violate = invariants (use assert).
language: python
category: error_handling
rule_id: ASSERT-NOT-VALIDATION
priority: error
tags:
- assertions
- validation
- correctness
---
Use assert for internal invariants (programmer errors). Use raise for
validation errors (user/external errors). Asserts can be disabled.
Preconditions on function parameters from external/user input =
validation (use raise). Preconditions on internal state that should
be impossible to violate = invariants (use assert).

## Good

- assert self._initialized  # Internal invariant
- if age < 0:
    raise ValueError('Age must be positive')  # Validation

## Bad

- assert age >= 0  # User input, must always check
