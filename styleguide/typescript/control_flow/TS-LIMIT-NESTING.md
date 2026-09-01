---
type: Styleguide Rule
description: |-
  Deeply nested code is hard to reason about. Refactor using early
  returns or extract functions if exceeding 3 levels.
language: typescript
category: control_flow
rule_id: TS-LIMIT-NESTING
priority: warn
tags:
- nesting
- complexity
- readability
---
Deeply nested code is hard to reason about. Refactor using early
returns or extract functions if exceeding 3 levels.

## Good

- if (a) {
  if (b) {
    if (c) return;
  }
}

## Bad

- if (a) {
  if (b) {
    if (c) {
      if (d) {
        // Too deep
      }
    }
  }
}
