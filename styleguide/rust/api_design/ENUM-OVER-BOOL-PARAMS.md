---
type: Styleguide Rule
description: |-
  Use an enum parameter instead of bool when the parameter's meaning is
  not obvious at the call site. If you do keep a bool, document it with an
  inline comment in the argument list.
language: rust
category: api_design
rule_id: ENUM-OVER-BOOL-PARAMS
priority: warn
tags:
- api-design
- parameters
- readability
- google-style
---
Use an enum parameter instead of bool when the parameter's meaning is
not obvious at the call site. If you do keep a bool, document it with an
inline comment in the argument list.

## Good

- pub enum Overwrite { Allow, Deny }

copy_file(src, dst, Overwrite::Deny)?;
- set_visible(true);
- copy_file(src, dst, /* overwrite= */ false)?;

## Bad

- copy_file(src, dst, false)?; // false what?
