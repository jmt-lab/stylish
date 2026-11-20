---
type: Styleguide Rule
description: |-
  Write extern blocks as unsafe extern (required in Rust 2024) and mark
  each item safe or unsafe. Mark a foreign function safe only if every
  possible argument is sound, so callers don't need an unsafe block for
  it.
language: rust
category: safety
rule_id: UNSAFE-EXTERN-BLOCKS
priority: error
tags:
- unsafe
- ffi
- edition-2024
- rust-skills
---
Write extern blocks as unsafe extern (required in Rust 2024) and mark
each item safe or unsafe. Mark a foreign function safe only if every
possible argument is sound, so callers don't need an unsafe block for
it.

## Good

- unsafe extern "C" {
    pub safe fn abs(value: i32) -> i32;
    pub unsafe fn strlen(text: *const c_char) -> usize;
}

## Bad

- extern "C" {
    fn abs(value: i32) -> i32;
    fn strlen(text: *const c_char) -> usize;
}
