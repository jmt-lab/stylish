---
type: Styleguide Rule
description: |-
  Complex types (100+ lines including impl blocks and trait impls,
  excluding doc comments) should get their own file named after the
  type (domain-specific). Simple related types can share a file.
  Avoid generic names like types.rs, models.rs, structs.rs.
language: rust
category: organization
rule_id: ONE-STRUCT-PER-FILE-COMPLEX
priority: info
tags:
- organization
- files
- carmack
---
Complex types (100+ lines including impl blocks and trait impls,
excluding doc comments) should get their own file named after the
type (domain-specific). Simple related types can share a file.
Avoid generic names like types.rs, models.rs, structs.rs.

## Good

- entity.rs // Just Entity
entity_manager.rs // Just EntityManager
user.rs // Just User

## Bad

- stuff.rs // Entity, EntityManager, Component, System all mixed
types.rs // Generic name
models.rs // Generic name
