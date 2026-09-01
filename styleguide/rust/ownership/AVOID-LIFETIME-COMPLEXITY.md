---
type: Styleguide Rule
description: |-
  If lifetime annotations get complex, consider restructuring.
  Simpler ownership patterns are easier to maintain.
language: rust
category: ownership
rule_id: AVOID-LIFETIME-COMPLEXITY
priority: warn
tags:
- ownership
- lifetimes
- complexity
- carmack
---
If lifetime annotations get complex, consider restructuring.
Simpler ownership patterns are easier to maintain.

## Good

- fn process(data: &Data) -> Result // Simple

## Bad

- fn complex<'a, 'b: 'a, 'c>(a: &'a T, b: &'b U, c: &'c V) -> &'a W
// Too complex
