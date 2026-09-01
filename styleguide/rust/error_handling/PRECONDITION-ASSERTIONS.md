---
type: Styleguide Rule
description: |-
  Every function should assert its preconditions at the start. This
  catches contract violations immediately.
language: rust
category: error_handling
rule_id: PRECONDITION-ASSERTIONS
priority: error
tags:
- assertions
- preconditions
- contracts
- carmack
---
Every function should assert its preconditions at the start. This
catches contract violations immediately.

## Good

- fn process(entity: &Entity) {
    assert!(!entity.is_dead());
    assert!(entity.health > 0.0);
    // ...
}

## Bad

- fn process(entity: &Entity) {
    // Hope entity is valid
}
