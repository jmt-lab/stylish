---
type: Styleguide Rule
description: |-
  Carmack principle: Deep nesting is hard to reason about.
  Use early returns or extract functions to reduce nesting.
language: rust
category: control_flow
rule_id: LIMIT-NESTING-DEPTH
priority: warn
tags:
- control-flow
- nesting
- carmack
---
Carmack principle: Deep nesting is hard to reason about.
Use early returns or extract functions to reduce nesting.

## Good

- // Max 3 levels
if a {
    if b {
        if c { return; }
    }
}

## Bad

- // Too deep
if a { if b { if c { if d { if e { ... } } } } }
