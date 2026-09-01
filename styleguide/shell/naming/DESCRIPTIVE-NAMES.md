---
type: Styleguide Rule
description: Variable and function names should be descriptive and meaningful.
language: shell
category: naming
rule_id: DESCRIPTIVE-NAMES
priority: warn
tags:
- naming
- clarity
---
Variable and function names should be descriptive and meaningful.

## Good

- local error_message='Failed to connect'
- process_user_input() { ... }

## Bad

- local em='Failed to connect'
- proc() { ... }
