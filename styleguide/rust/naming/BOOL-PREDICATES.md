---
type: Styleguide Rule
description: |-
  Boolean-returning functions should use predicate prefixes to make
  their return type obvious.
language: rust
category: naming
rule_id: BOOL-PREDICATES
priority: warn
tags:
- naming
- carmack
- booleans
- clarity
---
Boolean-returning functions should use predicate prefixes to make
their return type obvious.

## Good

- fn is_valid(&self) -> bool
- fn has_children(&self) -> bool
- fn can_move(&self) -> bool
- let should_render = true;

## Bad

- fn valid(&self) -> bool // Ambiguous
- fn children(&self) -> bool // Looks like getter
