---
type: Styleguide Rule
description: "Struct types and typedefs should end with _t to clearly distinguish \nthem from other identifiers."
language: language-agnostic
category: naming
rule_id: STRUCT-SUFFIX
priority: info
tags:
- structs
- typedefs
- clarity
---
Struct types and typedefs should end with _t to clearly distinguish 
them from other identifiers.

## Good

- renderEntity_t
- trace_t
- memblock_t

## Bad

- RenderEntity // No suffix
- trace // Could be function or variable
