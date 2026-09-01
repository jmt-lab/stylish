---
type: Styleguide Rule
description: |-
  Binary crates have main.rs with main function. Keep it thin,
  delegate to library code.
language: rust
category: organization
rule_id: MAIN-RS-BINARY
priority: warn
tags:
- organization
- binary
- official
---
Binary crates have main.rs with main function. Keep it thin,
delegate to library code.

## Good

- // main.rs
fn main() -> Result<()> {
    myapp::run()
}

## Bad

- // main.rs with 1000 lines of logic
