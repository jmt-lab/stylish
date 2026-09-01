---
type: Styleguide Rule
description: |-
  Prefer pure functions (no side effects, return values only) where possible.
  However, &mut parameters are correct when mutation is the function's explicit
  purpose (see EXCLUSIVE-BORROW-INTENT in ownership.yaml).
language: rust
category: functional
rule_id: PURE-FUNCTIONS
priority: warn
tags:
- functional
- purity
- carmack
---
Prefer pure functions (no side effects, return values only) where possible.
However, &mut parameters are correct when mutation is the function's explicit
purpose (see EXCLUSIVE-BORROW-INTENT in ownership.yaml).

## Good

- fn normalized(v: Vec3) -> Vec3 {
    let len = v.length();
    Vec3 { x: v.x/len, y: v.y/len, z: v.z/len }
}

## Bad

- fn add_offset(v: &mut Vec3, offset: f32) {
    v.x += offset; v.y += offset; v.z += offset;
    // Mutates when it could simply return a new Vec3
}
