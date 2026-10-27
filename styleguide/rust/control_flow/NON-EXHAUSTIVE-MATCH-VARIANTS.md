---
type: Styleguide Rule
description: |-
  When matching a #[non_exhaustive] enum, still list the known variants
  you don't handle in the wildcard arm (Variant | _ => ...) so it's clear
  they were considered. If you only care about specific variants, use if let
  or let ... else instead of a match.
language: rust
category: control_flow
rule_id: NON-EXHAUSTIVE-MATCH-VARIANTS
priority: info
tags:
- control-flow
- pattern-matching
- enums
- google-style
---
When matching a #[non_exhaustive] enum, still list the known variants
you don't handle in the wildcard arm (Variant | _ => ...) so it's clear
they were considered. If you only care about specific variants, use if let
or let ... else instead of a match.

## Good

- match shape {
    Shape::Circle => draw_circle(),
    Shape::Square => draw_square(),
    // Triangle and future variants need no action.
    Shape::Triangle | _ => {}
}
- if let Shape::Circle = shape {
    draw_circle();
}

## Bad

- match shape {
    Shape::Circle => draw_circle(),
    _ => {}
} // hides that Square and Triangle exist
