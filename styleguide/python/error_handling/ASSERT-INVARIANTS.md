---
type: Styleguide Rule
description: |-
  Use assert statements liberally to validate invariants and preconditions.
  These catch programmer errors during development. Preconditions on
  internal state that should be impossible to violate = invariants (use
  assert). Preconditions on function parameters from external/user input
  = validation (use raise).
language: python
category: error_handling
rule_id: ASSERT-INVARIANTS
priority: error
tags:
- assertions
- invariants
- preconditions
---
Use assert statements liberally to validate invariants and preconditions.
These catch programmer errors during development. Preconditions on
internal state that should be impossible to violate = invariants (use
assert). Preconditions on function parameters from external/user input
= validation (use raise).

## Good

- def process(entity):
    assert entity is not None
    assert entity.is_valid()
- assert 0 <= index < len(array)

## Bad

- def process(entity):
    # Hope entity is valid
    entity.update()
