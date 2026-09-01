---
type: Styleguide Rule
description: |-
  For non-boolean values, use explicit comparisons instead of relying
  on truthiness when intent matters.
language: typescript
category: control_flow
rule_id: TS-EXPLICIT-BOOLEAN
priority: info
tags:
- booleans
- clarity
- explicitness
---
For non-boolean values, use explicit comparisons instead of relying
on truthiness when intent matters.

## Good

- if (array.length > 0) { ... }
if (value !== null) { ... }

## Bad

- if (array.length) { ... } // Implicit
if (value) { ... } // Could be 0, '', etc.
