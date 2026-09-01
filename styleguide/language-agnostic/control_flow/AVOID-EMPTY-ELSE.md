---
type: Styleguide Rule
description: |-
  If the else block is empty or just a comment, restructure the
  condition or remove the else entirely.
language: language-agnostic
category: control_flow
rule_id: AVOID-EMPTY-ELSE
priority: info
tags:
- conditionals
- clarity
- noise
---
If the else block is empty or just a comment, restructure the
condition or remove the else entirely.

## Good

- if (condition) {
    DoSomething();
}

## Bad

- if (condition) {
    DoSomething();
} else {
    // Do nothing
}
