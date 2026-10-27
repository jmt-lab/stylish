---
type: Styleguide Rule
description: |-
  Expose each public item at exactly one path. Don't make a module public
  and also re-export its items elsewhere; pick one. A private (or pub(crate))
  module plus a single pub use is fine.
language: rust
category: api_design
rule_id: SINGLE-PUBLIC-PATH
priority: warn
tags:
- api-design
- modules
- re-exports
- beautiful-rust
---
Expose each public item at exactly one path. Don't make a module public
and also re-export its items elsewhere; pick one. A private (or pub(crate))
module plus a single pub use is fine.

## Good

- mod db;
pub use db::Connection;

## Bad

- pub mod db;
pub use db::Connection; // reachable as crate::Connection and crate::db::Connection
