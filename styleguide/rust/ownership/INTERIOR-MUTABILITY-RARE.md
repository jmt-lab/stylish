---
type: Styleguide Rule
description: |-
  Cell, RefCell, Mutex provide interior mutability. Use only when
  truly needed (caches, shared concurrent state). Document why.
  Do not use interior mutability for global mutable state — see
  AVOID-GLOBAL-MUTABLE-STATE in functional.yaml.
language: rust
category: ownership
rule_id: INTERIOR-MUTABILITY-RARE
priority: warn
tags:
- ownership
- interior-mutability
- patterns
---
Cell, RefCell, Mutex provide interior mutability. Use only when
truly needed (caches, shared concurrent state). Document why.
Do not use interior mutability for global mutable state — see
AVOID-GLOBAL-MUTABLE-STATE in functional.yaml.

## Good

- // Cache: needs interior mutability
struct Cache {
    data: RefCell<HashMap<Key, Value>>
}

## Bad

- // Don't use RefCell to avoid borrow checker
struct Entity {
    health: RefCell<f32> // Just use &mut
}
