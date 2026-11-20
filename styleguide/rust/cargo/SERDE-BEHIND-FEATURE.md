---
type: Styleguide Rule
description: |-
  Library crates make serde support an optional, additive feature (serde =
  ["dep:serde"]) instead of a hard dependency, unless serialization is the
  crate's purpose. Applications that don't serialize your types then don't
  compile serde for them.
language: rust
category: cargo
rule_id: SERDE-BEHIND-FEATURE
priority: warn
tags:
- cargo
- features
- serde
- libraries
- rust-skills
---
Library crates make serde support an optional, additive feature (serde =
["dep:serde"]) instead of a hard dependency, unless serialization is the
crate's purpose. Applications that don't serialize your types then don't
compile serde for them.

## Good

- [dependencies]
serde = { version = "1", features = ["derive"], optional = true }

[features]
serde = ["dep:serde"]

- #[derive(Debug, Clone)]
#[cfg_attr(feature = "serde", derive(serde::Serialize, serde::Deserialize))]
pub struct Coordinate { pub latitude: f64, pub longitude: f64 }

## Bad

- [dependencies]
serde = { version = "1", features = ["derive"] } # forced on every user
