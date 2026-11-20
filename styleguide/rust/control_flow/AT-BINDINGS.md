---
type: Styleguide Rule
description: |-
  Use @ bindings to name a value while also testing it against a pattern,
  rather than matching a range and then re-reading the original value.
language: rust
category: control_flow
rule_id: AT-BINDINGS
priority: info
tags:
- control-flow
- pattern-matching
- rust-skills
---
Use @ bindings to name a value while also testing it against a pattern,
rather than matching a range and then re-reading the original value.

## Good

- match status {
    code @ 500..=599 => retry(code),
    code @ 400..=499 => reject(code),
    _ => accept(),
}

## Bad

- match status {
    500..=599 => retry(status),
    400..=499 => reject(status),
    _ => accept(),
}
