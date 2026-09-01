---
type: Styleguide Rule
description: |-
  Document invariants that must hold, preconditions, and postconditions.
  This helps future maintainers understand constraints.
language: language-agnostic
category: comments
rule_id: COMMENT-INVARIANTS
priority: error
tags:
- invariants
- contracts
- safety
---
Document invariants that must hold, preconditions, and postconditions.
This helps future maintainers understand constraints.

## Good

- // Invariant: entityList is always sorted by ID
- // Precondition: buffer must be at least 256 bytes

## Bad

- // Does stuff
ProcessBuffer(buffer);
