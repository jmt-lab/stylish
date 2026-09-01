---
type: Styleguide Rule
description: Constants and static variables should use SCREAMING_SNAKE_CASE.
language: rust
category: naming
rule_id: SCREAMING-SNAKE-CONSTANTS
priority: error
pattern: ^[A-Z][A-Z0-9_]*$
tags:
- naming
- convention
- official
- carmack
---
Constants and static variables should use SCREAMING_SNAKE_CASE.

## Good

- const MAX_ENTITIES: usize = 1024;
- const FRAME_BUDGET_MS: f32 = 16.67;
- static GLOBAL_ALLOCATOR: Arena = Arena::new();

## Bad

- const maxEntities: usize = 1024;
- const max_entities: usize = 1024;
