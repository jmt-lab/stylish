---
type: Styleguide Rule
description: |-
  Small types (primitives, small aggregates) should implement Copy
  when appropriate. Makes usage more ergonomic.
language: rust
category: ownership
rule_id: COPY-TRAIT-SMALL-TYPES
priority: info
tags:
- ownership
- copy
- ergonomics
---
Small types (primitives, small aggregates) should implement Copy
when appropriate. Makes usage more ergonomic.

## Good

- #[derive(Copy, Clone)]
struct Vec3 { x: f32, y: f32, z: f32 }

## Bad

- // Vec3 without Copy requires .clone() everywhere
