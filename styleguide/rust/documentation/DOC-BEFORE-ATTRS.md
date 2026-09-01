---
type: Styleguide Rule
description: Doc comments should be placed before attributes.
language: rust
category: documentation
rule_id: DOC-BEFORE-ATTRS
priority: warn
tags:
- documentation
- attributes
- official
---
Doc comments should be placed before attributes.

## Good

- /// Documentation
#[inline]
fn process() {}

## Bad

- #[inline]
/// Documentation
fn process()
