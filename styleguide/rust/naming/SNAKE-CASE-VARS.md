---
type: Styleguide Rule
description: Variables, functions, methods, and modules should use snake_case naming.
language: rust
category: naming
rule_id: SNAKE-CASE-VARS
priority: error
pattern: ^[a-z][a-z0-9_]*$
tags:
- naming
- convention
- official
---
Variables, functions, methods, and modules should use snake_case naming.

## Good

- let my_variable = 5;
- fn calculate_sum() {}
- mod render_system;

## Bad

- let MyVariable = 5;
- fn CalculateSum() {}
