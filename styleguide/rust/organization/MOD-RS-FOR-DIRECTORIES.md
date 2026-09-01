---
type: Styleguide Rule
description: |-
  When a module has submodules, create a directory with mod.rs.
  Submodules go in separate files in that directory.
language: rust
category: organization
rule_id: MOD-RS-FOR-DIRECTORIES
priority: warn
tags:
- organization
- modules
- official
---
When a module has submodules, create a directory with mod.rs.
Submodules go in separate files in that directory.

## Good

- renderer/
  mod.rs // Public API
  backend.rs
  frontend.rs

## Bad

- renderer.rs // Can't have submodules
