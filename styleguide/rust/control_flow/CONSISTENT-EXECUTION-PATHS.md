---
type: Styleguide Rule
description: |-
  Carmack principle: Code that executes the same path most of
  the time is easier to understand and optimize.
language: rust
category: control_flow
rule_id: CONSISTENT-EXECUTION-PATHS
priority: info
tags:
- control-flow
- consistency
- carmack
---
Carmack principle: Code that executes the same path most of
the time is easier to understand and optimize.

## Good

- let result = compute();
if should_apply {
    apply(result);
}

## Bad

- if should_compute {
    let result = compute();
    apply(result);
}
