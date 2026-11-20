---
type: Styleguide Rule
description: |-
  Write attributes that can cause undefined behavior in their unsafe(...)
  form: #[unsafe(no_mangle)], #[unsafe(export_name = ...)], and
  #[unsafe(link_section = ...)]. Rust 2024 requires it, and it flags the
  symbol-collision risk for reviewers. Add a SAFETY comment explaining why
  the symbol is unique.
language: rust
category: safety
rule_id: UNSAFE-ATTRIBUTES
priority: error
tags:
- unsafe
- ffi
- edition-2024
- attributes
- rust-skills
---
Write attributes that can cause undefined behavior in their unsafe(...)
form: #[unsafe(no_mangle)], #[unsafe(export_name = ...)], and
#[unsafe(link_section = ...)]. Rust 2024 requires it, and it flags the
symbol-collision risk for reviewers. Add a SAFETY comment explaining why
the symbol is unique.

## Good

- // SAFETY: `plugin_init` is unique to this crate's exported symbols.
#[unsafe(no_mangle)]
pub extern "C" fn plugin_init() -> i32 { 0 }

## Bad

- #[no_mangle]
pub extern "C" fn plugin_init() -> i32 { 0 }
