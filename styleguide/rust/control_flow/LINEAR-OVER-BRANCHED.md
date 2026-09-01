---
type: Styleguide Rule
description: |-
  Carmack principle: Linear code is easier to read and optimize.
  Structure code to minimize branching when possible.
language: rust
category: control_flow
rule_id: LINEAR-OVER-BRANCHED
priority: info
tags:
- control-flow
- linearity
- carmack
---
Carmack principle: Linear code is easier to read and optimize.
Structure code to minimize branching when possible.

## Good

- let valid = validate();
let result = compute();
if valid { apply(result); }

## Bad

- if validate() {
    let result = compute();
    apply(result);
} // Variable execution
