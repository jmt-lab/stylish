---
type: Styleguide Rule
description: |-
  If else block is empty or just a comment, restructure the condition
  or remove the else.
language: typescript
category: control_flow
rule_id: TS-AVOID-EMPTY-ELSE
priority: info
tags:
- conditionals
- clarity
- noise
---
If else block is empty or just a comment, restructure the condition
or remove the else.

## Good

- if (condition) {
  doSomething();
}

## Bad

- if (condition) {
  doSomething();
} else {
  // Nothing
}
