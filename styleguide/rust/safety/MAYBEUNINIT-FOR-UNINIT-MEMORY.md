---
type: Styleguide Rule
description: |-
  Use MaybeUninit<T> for memory that is not yet initialized, and call
  assume_init only after every byte is written. Never use the deprecated
  mem::uninitialized, and never use mem::zeroed for types where all-zero
  bytes are invalid (references, NonZero, bool, enums, Box).
language: rust
category: safety
rule_id: MAYBEUNINIT-FOR-UNINIT-MEMORY
priority: error
tags:
- unsafe
- safety
- memory
- rust-skills
---
Use MaybeUninit<T> for memory that is not yet initialized, and call
assume_init only after every byte is written. Never use the deprecated
mem::uninitialized, and never use mem::zeroed for types where all-zero
bytes are invalid (references, NonZero, bool, enums, Box).

## Good

- let mut buffer = [const { MaybeUninit::<u8>::uninit() }; 4096];
let written = fill(&mut buffer);
// SAFETY: `fill` initialized the first `written` bytes.
let bytes = unsafe { buffer[..written].assume_init_ref() };

## Bad

- let mut buffer: [u8; 4096] = unsafe { std::mem::uninitialized() };
let handle: &Device = unsafe { std::mem::zeroed() }; // null reference: instant UB
