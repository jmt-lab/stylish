---
type: Styleguide Rule
description: |-
  When matching a single variant and ignoring others, if let
  is more concise than match.
language: rust
category: control_flow
rule_id: IF-LET-SINGLE-VARIANT
priority: info
tags:
- control-flow
- pattern-matching
- conciseness
---
When matching a single variant and ignoring others, if let
is more concise than match.

## Good

- if let Some(value) = option {
    process(value);
}

## Bad

- match option {
    Some(value) => process(value),
    None => {},
}
