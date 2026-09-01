---
type: Styleguide Rule
description: Setters should use 'set_' prefix to distinguish from getters.
language: rust
category: naming
rule_id: SETTER-WITH-SET-PREFIX
priority: warn
tags:
- naming
- convention
- setters
- official
---
Setters should use 'set_' prefix to distinguish from getters.

## Good

- fn set_health(&mut self, value: f32)
- fn set_position(&mut self, pos: Vec3)

## Bad

- fn health(&mut self, value: f32) // Ambiguous
