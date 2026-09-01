---
type: Styleguide Rule
description: |-
  Rust requires explicit .clone() calls. This makes expensive operations
  visible, preventing hidden performance issues.
language: rust
category: ownership
rule_id: CLONE-EXPLICIT
priority: error
tags:
- ownership
- performance
- explicitness
---
Rust requires explicit .clone() calls. This makes expensive operations
visible, preventing hidden performance issues.

## Good

- let copy = original.clone(); // Explicit

## Bad

- // C++ copy: Entity copy = original; // Hidden in Rust
