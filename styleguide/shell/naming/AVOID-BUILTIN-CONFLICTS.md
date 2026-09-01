---
type: Styleguide Rule
description: Don't use names that shadow built-in shell commands or common utilities.
language: shell
category: naming
rule_id: AVOID-BUILTIN-CONFLICTS
priority: error
tags:
- naming
- safety
---
Don't use names that shadow built-in shell commands or common utilities.

## Good

- my_test() { ... }
- check_status() { ... }

## Bad

- test() { ... }  # Conflicts with built-in test
- echo() { ... }  # Shadows echo command
