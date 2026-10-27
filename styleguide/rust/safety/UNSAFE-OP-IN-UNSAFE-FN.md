---
type: Styleguide Rule
description: |-
  Enable the unsafe_op_in_unsafe_fn lint so each unsafe operation inside
  an unsafe fn needs its own unsafe block with a SAFETY comment. Keep one
  unsafe operation per block (Clippy: multiple_unsafe_ops_per_block).
language: rust
category: safety
rule_id: UNSAFE-OP-IN-UNSAFE-FN
priority: warn
tags:
- safety
- unsafe
- lints
- beautiful-rust
---
Enable the unsafe_op_in_unsafe_fn lint so each unsafe operation inside
an unsafe fn needs its own unsafe block with a SAFETY comment. Keep one
unsafe operation per block (Clippy: multiple_unsafe_ops_per_block).

## Good

- pub unsafe fn read_header(ptr: *const u8) -> Header {
    // SAFETY: caller guarantees `ptr` points to HEADER_LEN readable bytes.
    let bytes = unsafe { slice::from_raw_parts(ptr, HEADER_LEN) };
    Header::parse(bytes)
}

## Bad

- pub unsafe fn read_header(ptr: *const u8) -> Header {
    let bytes = slice::from_raw_parts(ptr, HEADER_LEN); // implicitly unsafe, unexplained
    Header::parse(bytes)
}
