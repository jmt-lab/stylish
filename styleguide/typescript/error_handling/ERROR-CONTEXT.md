---
type: Styleguide Rule
description: |-
  Error messages should include relevant context (values, state) to aid
  debugging. Make errors actionable.
language: typescript
category: error_handling
rule_id: ERROR-CONTEXT
priority: warn
tags:
- debugging
- error-messages
- context
---
Error messages should include relevant context (values, state) to aid
debugging. Make errors actionable.

## Good

- throw new Error(`index ${i} out of bounds [0, ${arr.length})`)
- console.assert(x > 0, `x must be positive, got ${x}`);

## Bad

- throw new Error('invalid value'); // What value?
