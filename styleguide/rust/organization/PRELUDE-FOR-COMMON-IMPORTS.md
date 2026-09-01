---
type: Styleguide Rule
description: |-
  Create a prelude module for commonly used types and traits.
  Users can import with use crate::prelude::*.
language: rust
category: organization
rule_id: PRELUDE-FOR-COMMON-IMPORTS
priority: info
tags:
- organization
- prelude
- ergonomics
---
Create a prelude module for commonly used types and traits.
Users can import with use crate::prelude::*.

## Good

- // prelude.rs
pub use crate::{
    Entity, Component,
    Result, Error,
};

## Bad

- // Users import each type individually from deep paths
