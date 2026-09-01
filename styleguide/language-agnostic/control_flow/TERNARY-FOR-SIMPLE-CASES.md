---
type: Styleguide Rule
description: |-
  Ternary operator is fine for simple value selection. Don't use for
  complex expressions or side effects.
language: language-agnostic
category: control_flow
rule_id: TERNARY-FOR-SIMPLE-CASES
priority: info
tags:
- ternary
- conditionals
- clarity
---
Ternary operator is fine for simple value selection. Don't use for
complex expressions or side effects.

## Good

- result = (count > 0) ? count : 1; // Simple

## Bad

- result = (a > b) ? (c < d ? e : (f > g ? h : i)) : j; // Too complex
