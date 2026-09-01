---
type: Styleguide Rule
description: |-
  Document invariants that must hold, preconditions, postconditions,
  and assumptions. This helps maintainers understand constraints.
language: rust
category: comments
rule_id: INVARIANT-DOCUMENTATION
priority: warn
tags:
- invariants
- contracts
- carmack
---
Document invariants that must hold, preconditions, postconditions,
and assumptions. This helps maintainers understand constraints.

## Good

- /// Invariant: self.entities is always sorted by ID
struct EntityManager { ... }
- /// Precondition: buffer must be at least 256 bytes
fn process_buffer(buffer: &mut [u8])

## Bad

- fn process_buffer(buffer: &mut [u8]) // Size requirements?
