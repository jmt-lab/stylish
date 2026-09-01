---
type: Styleguide Rule
description: |-
  Use pub, pub(crate), pub(super) intentionally. Default (private)
  for implementation details, pub for public API.
language: rust
category: organization
rule_id: VISIBILITY-INTENTIONAL
priority: warn
tags:
- organization
- visibility
- api
---
Use pub, pub(crate), pub(super) intentionally. Default (private)
for implementation details, pub for public API.

## Good

- pub fn render() { ... } // Public API
pub(crate) fn internal_helper() { ... } // Crate-internal
fn private_impl() { ... } // Private

## Bad

- pub fn everything() { ... } // Everything public by default
