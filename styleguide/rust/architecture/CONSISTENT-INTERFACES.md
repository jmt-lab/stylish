---
type: Styleguide Rule
description: Define traits for types with similar behavior. Use the same method names and parameter orders for equivalent operations.
language: rust
category: architecture
rule_id: CONSISTENT-INTERFACES
priority: warn
tags:
- architecture
- api-design
- maintainability
---
Define traits for types with similar behavior. Use the same method names and parameter orders for equivalent operations.

## Good

- trait Repository { fn find(&self, id: Id) -> Result<T>; fn save(&mut self, item: T) -> Result<()>; }
