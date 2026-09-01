---
type: Styleguide Rule
description: |-
  Leverage Rust's exhaustive pattern matching. Exhaustive matching
  catches when new enum variants are added at compile time. Avoid
  catch-all _ when you want to handle all cases explicitly.
language: rust
category: control_flow
rule_id: EXHAUSTIVE-MATCH
priority: warn
tags:
- control-flow
- pattern-matching
- safety
- practices
---
Leverage Rust's exhaustive pattern matching. Exhaustive matching
catches when new enum variants are added at compile time. Avoid
catch-all _ when you want to handle all cases explicitly.

## Good

- match state {
    State::Init => { ... }
    State::Running => { ... }
    State::Stopped => { ... }
}

## Bad

- match state {
    State::Running => { ... }
    _ => {} // Hides new variants
}
