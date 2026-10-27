---
type: Styleguide Rule
description: |-
  Don't check a condition and then call a panicking accessor (unwrap,
  expect, indexing) that the check supposedly makes safe. Use pattern
  matching so the compiler proves the value exists.
language: rust
category: control_flow
rule_id: PATTERN-MATCH-OVER-CHECK-UNWRAP
priority: warn
tags:
- control-flow
- pattern-matching
- panics
- google-style
---
Don't check a condition and then call a panicking accessor (unwrap,
expect, indexing) that the check supposedly makes safe. Use pattern
matching so the compiler proves the value exists.

## Good

- if let Some(user) = maybe_user {
    greet(user);
}
- if let Some(first) = items.first() {
    process(first);
}

## Bad

- if maybe_user.is_some() {
    greet(maybe_user.unwrap());
}
- if !items.is_empty() {
    process(&items[0]);
}
