---
type: Styleguide Rule
description: Use only one derive attribute per item, combining multiple derives into a single attribute.
language: rust
category: attributes
rule_id: SINGLE-DERIVE
priority: warn
tags:
- attributes
- derive
---
Use only one derive attribute per item, combining multiple derives into a single attribute.

## Good

- #[derive(Debug, Clone, Copy)]

## Bad

- #[derive(Debug)]
#[derive(Clone)]
#[derive(Copy)]
