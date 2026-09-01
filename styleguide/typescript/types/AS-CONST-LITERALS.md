---
type: Styleguide Rule
description: |-
  Use 'as const' for literal values and object literals that should have
  narrow, deeply readonly types. This prevents widening, makes types more
  precise, and aligns with Carmack's const discipline.
language: typescript
category: types
rule_id: AS-CONST-LITERALS
priority: warn
tags:
- literals
- const
- precision
- immutability
- modern
---
Use 'as const' for literal values and object literals that should have
narrow, deeply readonly types. This prevents widening, makes types more
precise, and aligns with Carmack's const discipline.

## Good

- const DIRECTIONS = ['north', 'south', 'east', 'west'] as const;
- const config = { timeout: 5000, retries: 3 } as const;
- const CONFIG = { maxEntities: 1024 } as const;
- const COLORS = ['red', 'green', 'blue'] as const;

## Bad

- const DIRECTIONS = ['north', 'south', 'east', 'west']; // string[]
- const CONFIG = { maxEntities: 1024 }; // Mutable
- const COLORS = ['red', 'green', 'blue']; // Mutable array
