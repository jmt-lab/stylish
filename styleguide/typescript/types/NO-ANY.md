---
type: Styleguide Rule
description: |-
  Never use 'any' - it disables type checking. Use 'unknown' for truly
  unknown types, then narrow with type guards. 'any' is opting out of safety.
  When any is truly unavoidable (e.g., JSON.parse), prefer unknown with type
  narrowing. If any must be used, add a comment explaining why and suppress
  the lint rule inline.
language: typescript
category: types
rule_id: NO-ANY
priority: error
tags:
- types
- safety
- correctness
---
Never use 'any' - it disables type checking. Use 'unknown' for truly
unknown types, then narrow with type guards. 'any' is opting out of safety.
When any is truly unavoidable (e.g., JSON.parse), prefer unknown with type
narrowing. If any must be used, add a comment explaining why and suppress
the lint rule inline.

## Good

- function parse(input: unknown): Data
- const data: unknown = JSON.parse(str);

## Bad

- function parse(input: any): Data
- const data: any = JSON.parse(str);
