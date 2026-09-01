---
type: Styleguide Rule
description: |-
  Public APIs should clearly document ownership expectations,
  especially when they're non-obvious.
language: rust
category: ownership
rule_id: DOCUMENT-OWNERSHIP-CONTRACTS
priority: warn
tags:
- ownership
- documentation
- api
---
Public APIs should clearly document ownership expectations,
especially when they're non-obvious.

## Good

- /// Takes ownership of `data` and manages its lifetime.
/// The data will be freed when the manager is dropped.
fn register(data: Data)

## Bad

- fn register(data: Data) // What happens to data?
