---
type: Styleguide Rule
description: |-
  Break complex operations into small, pure functions that compose.
  Each function does one thing clearly.
language: typescript
category: functional
rule_id: FUNCTION-COMPOSITION
priority: info
tags:
- composition
- modularity
- purity
---
Break complex operations into small, pure functions that compose.
Each function does one thing clearly.

## Good

- const result = normalize(transform(filter(input)));
- const process = pipe(filter, transform, normalize);

## Bad

- function doEverything(input: Data): Result {
  // 100 lines of mixed logic
}
