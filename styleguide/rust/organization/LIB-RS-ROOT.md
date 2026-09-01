---
type: Styleguide Rule
description: |-
  Library crates should have lib.rs as the root, organizing
  modules and defining the public API.
language: rust
category: organization
rule_id: LIB-RS-ROOT
priority: error
tags:
- organization
- library
- official
---
Library crates should have lib.rs as the root, organizing
modules and defining the public API.

## Good

- // lib.rs
pub mod renderer;
pub mod audio;

pub use renderer::Renderer;

## Bad

- // No lib.rs, unclear entry point
