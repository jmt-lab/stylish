---
type: Styleguide Rule
description: |-
  Structure data for how it's accessed. Keep hot data together,
  use #[repr(C)] for predictable layout, consider struct-of-arrays.
language: rust
category: optimization
rule_id: CACHE-FRIENDLY-LAYOUT
priority: warn
tags:
- optimization
- cache
- dod
- carmack
---
Structure data for how it's accessed. Keep hot data together,
use #[repr(C)] for predictable layout, consider struct-of-arrays.

## Good

- // Structure-of-arrays: all positions contiguous
struct Entities {
    positions: Vec<Vec3>,
    velocities: Vec<Vec3>,
}

## Bad

- // Array-of-structures: positions scattered
struct Entity {
    position: Vec3,
    // ... 100 other fields
}
let entities: Vec<Entity>;
