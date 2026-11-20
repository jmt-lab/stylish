---
type: Styleguide Rule
description: |-
  Use matches! to test whether a value fits a pattern when you only need a
  bool, instead of a match or if let that returns true and false.
language: rust
category: control_flow
rule_id: MATCHES-MACRO-FOR-BOOLEAN-TESTS
priority: info
tags:
- control-flow
- pattern-matching
- idioms
- rust-skills
---
Use matches! to test whether a value fits a pattern when you only need a
bool, instead of a match or if let that returns true and false.

## Good

- let is_terminal = matches!(state, State::Done | State::Failed { .. });

## Bad

- let is_terminal = match state {
    State::Done | State::Failed { .. } => true,
    _ => false,
};
