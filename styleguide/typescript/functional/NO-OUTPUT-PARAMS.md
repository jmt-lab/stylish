---
type: Styleguide Rule
description: |-
  Functions should return results, not write to mutable parameters.
  Return values make data flow obvious and enable composition.
language: typescript
category: functional
rule_id: NO-OUTPUT-PARAMS
priority: warn
tags:
- parameters
- data-flow
- return-values
---
Functions should return results, not write to mutable parameters.
Return values make data flow obvious and enable composition.

## Good

- function parse(input: string): Result
- function transform(data: Data): [Output, Error | null]

## Bad

- function parse(input: string, output: Result): void
- function transform(data: Data, output: Output, error: Error): void
