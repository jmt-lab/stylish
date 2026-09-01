---
type: Styleguide Rule
description: |-
  Carmack's subsystem organization translates to Rust modules. Major
  subsystems should be separate modules with clear responsibilities.
language: rust
category: organization
rule_id: MODULE-PER-SUBSYSTEM
priority: warn
tags:
- organization
- modules
- carmack
---
Carmack's subsystem organization translates to Rust modules. Major
subsystems should be separate modules with clear responsibilities.

## Good

- src/
  renderer/
    mod.rs
    backend.rs
  audio/
    mod.rs
  game/
    mod.rs

## Bad

- src/
  utils.rs
  misc.rs
  stuff.rs
