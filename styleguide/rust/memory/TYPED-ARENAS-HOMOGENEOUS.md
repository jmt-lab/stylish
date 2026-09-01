---
type: Styleguide Rule
description: |-
  When allocating many instances of the same type with the same
  lifetime, use typed-arena for optimal performance.
language: rust
category: memory
rule_id: TYPED-ARENAS-HOMOGENEOUS
priority: info
tags:
- memory
- allocators
- performance
---
When allocating many instances of the same type with the same
lifetime, use typed-arena for optimal performance.

## Good

- use typed_arena::Arena;

let entity_arena = Arena::new();
let entity = entity_arena.alloc(Entity::new());
// All entities freed together

## Bad

- let mut entities = Vec::new();
for _ in 0..1000 {
    entities.push(Box::new(Entity::new()));
}
