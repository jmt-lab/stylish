---
type: Styleguide Rule
description: |-
  Give magic values a named const with a doc comment saying where the
  value comes from, what changing it affects, and any external system that
  depends on it.
language: rust
category: documentation
rule_id: DOCUMENT-MAGIC-VALUES
priority: warn
tags:
- documentation
- constants
- beautiful-rust
---
Give magic values a named const with a doc comment saying where the
value comes from, what changing it affects, and any external system that
depends on it.

## Good

- /// Maximum payload accepted by the upstream gateway (see its API limits).
/// Raising it causes 413 responses from the gateway.
const MAX_PAYLOAD_BYTES: usize = 6 * 1024 * 1024;

## Bad

- const MAX_PAYLOAD_BYTES: usize = 6291456;
- if body.len() > 6291456 { ... }
