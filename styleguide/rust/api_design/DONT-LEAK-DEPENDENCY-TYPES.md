---
type: Styleguide Rule
description: |-
  Prefer std types in public APIs; a third-party type in a signature ties
  your semver to that crate's. Expose one only behind a feature (e.g. serde)
  or for substantial benefit, and then re-export the crate so callers can
  name the matching version. Don't pub use another crate's items otherwise.
language: rust
category: api_design
rule_id: DONT-LEAK-DEPENDENCY-TYPES
priority: warn
tags:
- api-design
- dependencies
- semver
- beautiful-rust
---
Prefer std types in public APIs; a third-party type in a signature ties
your semver to that crate's. Expose one only behind a feature (e.g. serde)
or for substantial benefit, and then re-export the crate so callers can
name the matching version. Don't pub use another crate's items otherwise.

## Good

- pub fn timeout(&self) -> Duration { ... }

#[cfg(feature = "chrono")]
pub use chrono;

## Bad

- pub fn timeout(&self) -> chrono::Duration { ... } // forces chrono on every caller
- pub use tokio::sync::Mutex; // re-exporting a foreign item as part of your API
