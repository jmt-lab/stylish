---
type: Styleguide Rule
description: |-
  When code paths are provably impossible, use unreachable!() with
  explanation. Better than silent panic or undefined behavior.
language: rust
category: error_handling
rule_id: UNREACHABLE-EXPLICIT
priority: warn
tags:
- errors
- unreachable
- safety
---
When code paths are provably impossible, use unreachable!() with
explanation. Better than silent panic or undefined behavior.

## Good

- match state {
    State::Running => { ... }
    State::Stopped => unreachable!("tick() called on stopped game")
}

## Bad

- match state {
    State::Running => { ... }
    // Missing stopped case, silent UB
}
