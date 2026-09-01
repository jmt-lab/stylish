---
type: Styleguide Rule
description: "Boolean variables and functions should use predicate prefixes to make \ntheir type and intent obvious. Aligns with Carmack's BOOL-PREDICATES."
language: typescript
category: naming
rule_id: TS-BOOL-PREFIX
priority: info
tags:
- booleans
- clarity
---
Boolean variables and functions should use predicate prefixes to make 
their type and intent obvious. Aligns with Carmack's BOOL-PREDICATES.

## Good

- const isValid = true;
- function hasChildren(): boolean {}
- const canRender = entity.isVisible;
- const shouldUpdate = deltaTime > 0;

## Bad

- const valid = true; // Ambiguous
- function children(): boolean {} // Unclear
