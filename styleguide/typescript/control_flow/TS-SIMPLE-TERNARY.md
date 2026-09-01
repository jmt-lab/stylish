---
type: Styleguide Rule
description: |-
  Ternary operator is fine for simple value selection. Avoid nested
  or complex ternaries.
language: typescript
category: control_flow
rule_id: TS-SIMPLE-TERNARY
priority: warn
tags:
- ternary
- conditionals
- clarity
---
Ternary operator is fine for simple value selection. Avoid nested
or complex ternaries.

## Good

- const label = isActive ? 'On' : 'Off';

## Bad

- const x = a ? (b ? (c ? d : e) : f) : g; // Too complex
