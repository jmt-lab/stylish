---
type: Styleguide Rule
description: |-
  Generate FFI declarations with bindgen (or cxx for C++) in a raw foo-sys
  crate, and keep business logic in a safe foo crate on top. Name crates that
  export Rust as a C library foo-ffi. Fail CI if regenerated bindings differ
  from the committed ones.
language: rust
category: safety
rule_id: SYS-CRATE-SPLIT
priority: info
tags:
- safety
- ffi
- bindgen
- organization
- beautiful-rust
---
Generate FFI declarations with bindgen (or cxx for C++) in a raw foo-sys
crate, and keep business logic in a safe foo crate on top. Name crates that
export Rust as a C library foo-ffi. Fail CI if regenerated bindings differ
from the committed ones.

## Good

- crates/
  zstd-sys/   # bindgen output, links libzstd
  zstd/       # safe wrapper API

## Bad

- // src/lib.rs: 400 hand-written extern "C" declarations mixed with business logic
