---
type: Styleguide Rule
description: |-
  Every module should have module-level doc comments (//!) explaining
  its purpose and how it fits into the system. Describe component
  interactions and the module's role in the overall architecture.
language: rust
category: comments
rule_id: MODULE-LEVEL-DOCS
priority: warn
tags:
- documentation
- modules
- organization
---
Every module should have module-level doc comments (//!) explaining
its purpose and how it fits into the system. Describe component
interactions and the module's role in the overall architecture.

## Good

- //! Renderer subsystem.
//!
//! Handles all rendering operations including scene setup,
//! culling, and GPU command submission.


## Bad

- // renderer.rs with no module docs
