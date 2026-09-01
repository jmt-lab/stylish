---
type: Styleguide Rule
description: |-
  When checking multiple conditions, match is clearer than
  nested if-let chains.
language: rust
category: control_flow
rule_id: MATCH-OVER-IF-LET-CHAIN
priority: info
tags:
- control-flow
- pattern-matching
- clarity
---
When checking multiple conditions, match is clearer than
nested if-let chains.

## Good

- match (option_a, option_b) {
    (Some(a), Some(b)) => process(a, b),
    _ => default(),
}

## Bad

- if let Some(a) = option_a {
    if let Some(b) = option_b {
        process(a, b);
    }
}
