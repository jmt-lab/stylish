---
type: Styleguide Rule
description: |-
  Mark enums that are part of a public API used by other teams
  #[non_exhaustive] so adding a variant isn't a breaking change. Exceptions:
  enums that will never change (a fixed ontology like Color { Red, Green,
  Blue }, or a two-state bool replacement), or when you commit to fixing all
  breakages yourself (Clippy: exhaustive_enums).
language: rust
category: api_design
rule_id: NON-EXHAUSTIVE-PUBLIC-ENUMS
priority: warn
tags:
- api-design
- enums
- compatibility
- semver
- google-style
---
Mark enums that are part of a public API used by other teams
#[non_exhaustive] so adding a variant isn't a breaking change. Exceptions:
enums that will never change (a fixed ontology like Color { Red, Green,
Blue }, or a two-state bool replacement), or when you commit to fixing all
breakages yourself (Clippy: exhaustive_enums).

## Good

- #[non_exhaustive]
pub enum RequestError {
    Timeout,
    ConnectionReset,
    InvalidResponse,
}
- pub enum Visibility { Visible, Hidden } // will never grow

## Bad

- pub enum RequestError {
    Timeout,
    ConnectionReset,
} // adding a variant breaks every downstream match
