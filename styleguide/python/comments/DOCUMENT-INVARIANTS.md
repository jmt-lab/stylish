---
type: Styleguide Rule
description: Document class invariants, preconditions, postconditions, and assumptions. This helps maintainers understand constraints.
language: python
category: comments
rule_id: DOCUMENT-INVARIANTS
priority: warn
tags:
- invariants
- contracts
- safety
---
Document class invariants, preconditions, postconditions, and assumptions. This helps maintainers understand constraints.

## Good

- # Invariant: self._cache is always sorted by timestamp
- # Precondition: buffer must be non-empty
- # Assumes UTF-8 encoding
