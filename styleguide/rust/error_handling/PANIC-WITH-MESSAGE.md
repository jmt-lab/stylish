---
type: Styleguide Rule
description: |-
  When using panic!, always include a descriptive message. Helps
  debugging by explaining what went wrong.
language: rust
category: error_handling
rule_id: PANIC-WITH-MESSAGE
priority: warn
tags:
- panic
- debugging
- messages
---
When using panic!, always include a descriptive message. Helps
debugging by explaining what went wrong.

## Good

- panic!("Entity ID {} not found in registry", id);

## Bad

- panic!(); // No information about failure
