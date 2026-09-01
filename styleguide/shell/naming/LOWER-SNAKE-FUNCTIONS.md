---
type: Styleguide Rule
description: Function names should be lowercase with underscores separating words.
language: shell
category: naming
rule_id: LOWER-SNAKE-FUNCTIONS
priority: error
pattern: ^[a-z][a-z0-9_]*$
tags:
- naming
- functions
---
Function names should be lowercase with underscores separating words.

## Good

- function my_func() { ... }
- process_data() { ... }

## Bad

- function MyFunc() { ... }
- function myFunc() { ... }
