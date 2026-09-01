---
type: Styleguide Rule
description: |-
  Do not use Python built-in names as variable or function names. This
  causes confusion and bugs.
language: python
category: naming
rule_id: AVOID-BUILTIN-SHADOWS
priority: error
tags:
- variables
- antipattern
- correctness
---
Do not use Python built-in names as variable or function names. This
causes confusion and bugs.

## Good

- items_list = []
- type_name = 'entity'
- id_number = 42

## Bad

- list = [] # Shadows built-in
- type = 'entity' # Shadows built-in
- id = 42 # Shadows built-in
