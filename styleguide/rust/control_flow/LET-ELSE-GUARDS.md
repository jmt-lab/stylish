---
type: Styleguide Rule
description: |-
  Rust 1.65+ let-else enables clean guard patterns with
  early return for None/Err.
language: rust
category: control_flow
rule_id: LET-ELSE-GUARDS
priority: info
tags:
- control-flow
- pattern-matching
- rust-2021
---
Rust 1.65+ let-else enables clean guard patterns with
early return for None/Err.

## Good

- fn process(id: EntityId) -> Result<()> {
    let Some(entity) = find_entity(id) else {
        return Err(Error::NotFound);
    };
    // Use entity
}

## Bad

- fn process(id: EntityId) -> Result<()> {
    match find_entity(id) {
        Some(entity) => { /* nested */ },
        None => return Err(Error::NotFound),
    }
}
