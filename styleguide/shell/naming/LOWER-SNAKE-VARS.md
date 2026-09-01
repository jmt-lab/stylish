---
type: Styleguide Rule
description: Local variables should be lowercase with underscores.
language: shell
category: naming
rule_id: LOWER-SNAKE-VARS
priority: error
pattern: ^[a-z][a-z0-9_]*$
tags:
- naming
- variables
---
Local variables should be lowercase with underscores.

## Good

- local my_var='value'
- local file_count=0

## Bad

- local MyVar='value'
- local myVar='value'
