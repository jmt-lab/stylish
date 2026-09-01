---
type: Styleguide Rule
description: |-
  Use assertions to validate invariants and catch programmer errors.
  Assertions should be plentiful in debug builds to catch bugs early.
  Programmer errors (assertion failures, invalid states) should cause
  immediate termination in debug builds — fail fast, don't try to
  recover from logic bugs. Hiding invalid state by substituting
  defaults masks the real problem.
language: language-agnostic
category: error_handling
rule_id: ASSERT-INVARIANTS
priority: error
tags:
- assertions
- invariants
- safety
- debugging
- correctness
- fail-fast
---
Use assertions to validate invariants and catch programmer errors.
Assertions should be plentiful in debug builds to catch bugs early.
Programmer errors (assertion failures, invalid states) should cause
immediate termination in debug builds — fail fast, don't try to
recover from logic bugs. Hiding invalid state by substituting
defaults masks the real problem.

## Good

- assert(entity != NULL);
- assert(index < array.size());
- assert(count >= 0 && count <= MAX_COUNT);
- if (!invariant_holds()) { abort(); }

## Bad

- // No assertion, assumes entity is valid
entity->Update();
- if (ptr == NULL) { ptr = &default; } // Hiding bug
