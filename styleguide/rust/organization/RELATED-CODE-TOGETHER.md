---
type: Styleguide Rule
description: |-
  Carmack principle: Keep related functions, types, and implementations
  near each other in the file.
language: rust
category: organization
rule_id: RELATED-CODE-TOGETHER
priority: info
tags:
- organization
- cohesion
- carmack
---
Carmack principle: Keep related functions, types, and implementations
near each other in the file.

## Good

- // All Vec3 code together
struct Vec3 { ... }
impl Vec3 { ... }
impl Add for Vec3 { ... }

## Bad

- // Vec3 scattered across file
