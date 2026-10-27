---
type: Styleguide Rule
description: |-
  Mark public structs with all-public fields that are used by other teams
  #[non_exhaustive], so new fields can be added without breaking struct
  literals. Exceptions: fields that will never change (e.g. a Rectangle), you
  commit to fixing breakages yourself, or you want callers to use
  functional record update (..Default::default()).
language: rust
category: api_design
rule_id: NON-EXHAUSTIVE-PUBLIC-STRUCTS
priority: warn
tags:
- api-design
- structs
- compatibility
- semver
- google-style
---
Mark public structs with all-public fields that are used by other teams
#[non_exhaustive], so new fields can be added without breaking struct
literals. Exceptions: fields that will never change (e.g. a Rectangle), you
commit to fixing breakages yourself, or you want callers to use
functional record update (..Default::default()).

## Good

- #[non_exhaustive]
pub struct ServerInfo {
    pub version: String,
    pub uptime: Duration,
}
- pub struct Rectangle { pub width: u32, pub height: u32 } // fixed shape

## Bad

- pub struct ServerInfo {
    pub version: String,
    pub uptime: Duration,
} // adding a field breaks every ServerInfo { .. } literal downstream
