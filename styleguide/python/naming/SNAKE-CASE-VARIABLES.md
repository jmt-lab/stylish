---
type: Styleguide Rule
description: |-
  Local variables, function parameters, and module-level variables should
  use lowercase with underscores.
language: python
category: naming
rule_id: SNAKE-CASE-VARIABLES
priority: error
tags:
- variables
- pep8
---
Local variables, function parameters, and module-level variables should
use lowercase with underscores.

## Good

- entity_number = 42
- frame_count = 0
- delta_time = 0.016

## Bad

- entityNumber = 42 # camelCase
- FrameCount = 0 # PascalCase
