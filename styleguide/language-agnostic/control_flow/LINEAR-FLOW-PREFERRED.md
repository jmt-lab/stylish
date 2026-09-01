---
type: Styleguide Rule
description: |-
  When possible, structure code to flow linearly rather than branching
  heavily. This improves readability and performance.
language: language-agnostic
category: control_flow
rule_id: LINEAR-FLOW-PREFERRED
priority: info
tags:
- linearity
- flow
- performance
---
When possible, structure code to flow linearly rather than branching
heavily. This improves readability and performance.

## Good

- // Linear with flags
enabled = CheckEnabled();
result = Process();
if (enabled) Apply(result);

## Bad

- // Heavy branching
if (enabled) { result = Process(); Apply(result); }
