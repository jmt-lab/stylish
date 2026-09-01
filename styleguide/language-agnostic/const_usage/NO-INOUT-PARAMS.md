---
type: Styleguide Rule
description: |-
  Parameters should be either input (const) or output (non-const), never
  both. This makes data flow explicit and obvious.
language: language-agnostic
category: const_usage
rule_id: NO-INOUT-PARAMS
priority: error
tags:
- parameters
- data-flow
- clarity
---
Parameters should be either input (const) or output (non-const), never
both. This makes data flow explicit and obvious.

## Good

- void Transform(const Vector3* input, Vector3* output);

## Bad

- void Transform(Vector3* inOut); // Unclear direction
