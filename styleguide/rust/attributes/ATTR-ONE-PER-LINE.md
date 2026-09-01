---
type: Styleguide Rule
description: Each attribute should be on its own line, indented to the item's level.
language: rust
category: attributes
rule_id: ATTR-ONE-PER-LINE
priority: warn
tags:
- attributes
- formatting
---
Each attribute should be on its own line, indented to the item's level.

## Good

- #[repr(C)]
#[derive(Debug)]
struct Foo {}

## Bad

- #[repr(C)] #[derive(Debug)]
struct Foo {}
