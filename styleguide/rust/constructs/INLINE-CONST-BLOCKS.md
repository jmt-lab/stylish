---
type: Styleguide Rule
description: |-
  Use inline const { ... } blocks (Rust 1.79+) to force compile-time
  evaluation inside an expression: array repeat expressions of non-Copy
  values, thread_local initializers, and compile-time assertions in
  generic code.
language: rust
category: constructs
rule_id: INLINE-CONST-BLOCKS
priority: info
tags:
- constants
- compile-time
- rust-skills
---
Use inline const { ... } blocks (Rust 1.79+) to force compile-time
evaluation inside an expression: array repeat expressions of non-Copy
values, thread_local initializers, and compile-time assertions in
generic code.

## Good

- let mut buckets: [Vec<Entry>; 16] = [const { Vec::new() }; 16];

- fn as_chunks<const N: usize>(bytes: &[u8]) -> &[[u8; N]] {
    const { assert!(N > 0, "chunk size must be non-zero") };
    // ...
}

## Bad

- let mut buckets: [Vec<Entry>; 16] = Default::default(); // verbose, size-limited

- fn as_chunks<const N: usize>(bytes: &[u8]) -> &[[u8; N]] {
    assert!(N > 0); // checked at runtime on every call
    // ...
}
