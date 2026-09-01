---
type: Styleguide Rule
description: Do not use the bon crate for newtypes (single-field tuple structs) as it adds unnecessary complexity
language: rust
category: constructs
rule_id: AVOID-BON-NEWTYPES
priority: error
tags:
- newtypes
- builders
- complexity
---
Do not use the bon crate for newtypes (single-field tuple structs) as it adds unnecessary complexity

## Good

- struct UserId(u64);
- struct Email(String);

## Bad

- #[derive(bon::Builder)]
struct UserId(u64);
