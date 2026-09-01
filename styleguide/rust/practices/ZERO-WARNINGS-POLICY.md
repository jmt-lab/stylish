---
type: Styleguide Rule
description: |-
  Code should compile with zero warnings. Fix warnings immediately,
  don't let them accumulate.
language: rust
category: practices
rule_id: ZERO-WARNINGS-POLICY
priority: error
tags:
- practices
- warnings
- carmack
---
Code should compile with zero warnings. Fix warnings immediately,
don't let them accumulate.

## Good

- # Build output: 0 warnings

## Bad

- # 234 warnings (what's one more?)
