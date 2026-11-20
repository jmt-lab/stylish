---
type: Styleguide Rule
description: |-
  Don't suffix or prefix crate names with -rs or -rust. Every crate on
  crates.io is Rust, so the affix adds nothing and makes the import path
  awkward. Use hyphens in the package name; Cargo maps them to underscores
  in code.
language: rust
category: naming
rule_id: CRATE-NAME-NO-RS-SUFFIX
priority: info
tags:
- naming
- cargo
- crates
- rust-skills
---
Don't suffix or prefix crate names with -rs or -rust. Every crate on
crates.io is Rust, so the affix adds nothing and makes the import path
awkward. Use hyphens in the package name; Cargo maps them to underscores
in code.

## Good

- [package]
name = "image-resize"

## Bad

- [package]
name = "image-resize-rs"
