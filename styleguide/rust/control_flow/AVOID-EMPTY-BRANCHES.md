---
type: Styleguide Rule
description: |-
  If the else branch is empty, restructure or remove it.
  Empty branches add noise.
language: rust
category: control_flow
rule_id: AVOID-EMPTY-BRANCHES
priority: info
tags:
- control-flow
- clarity
- carmack
---
If the else branch is empty, restructure or remove it.
Empty branches add noise.

## Good

- if condition {
    do_something();
}

## Bad

- if condition {
    do_something();
} else {
    // Do nothing
}
