---
type: Styleguide Rule
description: |-
  When a function takes ownership (parameter type T), the transfer
  is explicit. Document when ownership is transferred.
language: rust
category: ownership
rule_id: OWNERSHIP-TRANSFER-EXPLICIT
priority: warn
tags:
- ownership
- documentation
- clarity
---
When a function takes ownership (parameter type T), the transfer
is explicit. Document when ownership is transferred.

## Good

- /// Takes ownership of the entity
fn consume_entity(entity: Entity)
- /// Returns owned data
fn create_buffer() -> Vec<u8>

## Bad

- fn process(entity: Entity) // No doc about ownership
