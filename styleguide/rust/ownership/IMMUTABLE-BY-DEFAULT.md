---
type: Styleguide Rule
description: |-
  Rust enforces Carmack's 'const everything' principle. Variables are
  immutable unless explicitly marked mut. Only add mut when necessary.
language: rust
category: ownership
rule_id: IMMUTABLE-BY-DEFAULT
priority: error
tags:
- ownership
- immutability
- carmack
---
Rust enforces Carmack's 'const everything' principle. Variables are
immutable unless explicitly marked mut. Only add mut when necessary.

## Good

- let count = entities.len(); // Immutable by default
- let mut position = Vec3::ZERO; // Explicit mutability

## Bad

- // Don't add mut unnecessarily
let mut count = entities.len(); // Never modified
