---
type: Styleguide Rule
description: |-
  Prefer return values over output parameters when possible, but
  separated input (const) / output (non-const) parameters are acceptable
  when multiple outputs are needed (see NO-INOUT-PARAMS in
  const_usage.yaml). The key concern is hidden data flow — a single
  return value is clearest, but explicit output parameters with clear
  const separation are preferable to in-out parameters.
language: language-agnostic
category: functional_patterns
rule_id: AVOID-OUTPUT-PARAMS
priority: warn
tags:
- parameters
- data-flow
- composition
---
Prefer return values over output parameters when possible, but
separated input (const) / output (non-const) parameters are acceptable
when multiple outputs are needed (see NO-INOUT-PARAMS in
const_usage.yaml). The key concern is hidden data flow — a single
return value is clearest, but explicit output parameters with clear
const separation are preferable to in-out parameters.

## Good

- Result r = Process(input); // Clear data flow
- void Transform(const Vector3* input, Vector3* output); // Acceptable: separated in/out

## Bad

- void Process(Vector3* inOut); // In-out parameter hides data flow
