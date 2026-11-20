---
type: Styleguide Rule
description: |-
  Mark a single-field newtype #[repr(transparent)] when it crosses an FFI
  boundary or is transmuted or pointer-cast to its inner type. Without it,
  Rust guarantees nothing about the newtype's layout or ABI.
language: rust
category: safety
rule_id: REPR-TRANSPARENT-FFI-NEWTYPES
priority: warn
tags:
- unsafe
- ffi
- newtypes
- layout
- rust-skills
---
Mark a single-field newtype #[repr(transparent)] when it crosses an FFI
boundary or is transmuted or pointer-cast to its inner type. Without it,
Rust guarantees nothing about the newtype's layout or ABI.

## Good

- #[repr(transparent)]
pub struct FileDescriptor(c_int);

unsafe extern "C" {
    safe fn close(descriptor: FileDescriptor) -> c_int;
}

## Bad

- pub struct FileDescriptor(c_int); // default repr: ABI not guaranteed

unsafe extern "C" {
    fn close(descriptor: FileDescriptor) -> c_int;
}
