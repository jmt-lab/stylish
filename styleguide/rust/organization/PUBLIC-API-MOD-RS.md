---
type: Styleguide Rule
description: |-
  The mod.rs file should define the public interface of a module,
  re-exporting items and organizing submodules.
language: rust
category: organization
rule_id: PUBLIC-API-MOD-RS
priority: warn
tags:
- organization
- api
- visibility
---
The mod.rs file should define the public interface of a module,
re-exporting items and organizing submodules.

## Good

- // renderer/mod.rs
mod backend;
mod frontend;

pub use frontend::{RenderScene, RenderState};
pub(crate) use backend::GpuContext;

## Bad

- // mod.rs with no organization, everything public
