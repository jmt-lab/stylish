---
type: Styleguide Rule
description: |-
  Data processed with SIMD should be appropriately aligned. Use
  repr(align(N)) for guaranteed alignment.
language: rust
category: memory
rule_id: MEM-ALIGN-SIMD
priority: info
tags:
- memory
- alignment
- simd
- carmack
---
Data processed with SIMD should be appropriately aligned. Use
repr(align(N)) for guaranteed alignment.

## Good

- #[repr(align(16))]
struct Vec4 { x: f32, y: f32, z: f32, w: f32 }

## Bad

- struct Vec4 { x: f32, y: f32, z: f32, w: f32 } // May be misaligned
