---
type: Styleguide Rule
description: |-
  Carmack's frame allocators translate directly to Rust arena patterns.
  Use bumpalo or typed-arena for temporary, scope-based allocations.
language: rust
category: memory
rule_id: ARENA-ALLOCATORS
priority: warn
tags:
- memory
- allocators
- carmack
- performance
---
Carmack's frame allocators translate directly to Rust arena patterns.
Use bumpalo or typed-arena for temporary, scope-based allocations.

## Good

- use bumpalo::Bump;

let arena = Bump::new();
let temp_data = arena.alloc_slice_copy(slice);
// All arena allocations freed when arena drops

## Bad

- let temp_data = vec![0; size]; // Heap allocation for temp data
