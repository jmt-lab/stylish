---
type: Styleguide Rule
description: |-
  Document invariants that must hold, preconditions, postconditions,
  and assumptions about state. This helps maintainers understand constraints.
language: typescript
category: comments
rule_id: DOCUMENT-INVARIANTS
priority: warn
tags:
- invariants
- contracts
- safety
---
Document invariants that must hold, preconditions, postconditions,
and assumptions about state. This helps maintainers understand constraints.

## Good

- // Invariant: items array is always sorted by timestamp
- // Precondition: user must be authenticated
- // Assumes: DOM is fully loaded

## Bad

- // Process items processItems(items);
