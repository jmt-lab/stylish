---
type: Styleguide Rule
description: |-
  Rust convention: simple field getters don't need 'get_' prefix.
  Use the field name directly.
language: rust
category: naming
rule_id: GETTER-WITHOUT-GET-PREFIX
priority: warn
tags:
- naming
- convention
- getters
- official
---
Rust convention: simple field getters don't need 'get_' prefix.
Use the field name directly.

## Good

- fn name(&self) -> &str { &self.name }
- fn health(&self) -> f32 { self.health }

## Bad

- fn get_name(&self) -> &str { &self.name }
- fn get_health(&self) -> f32 { self.health }
