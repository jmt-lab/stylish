---
type: Styleguide Rule
description: |-
  Write any instead of interface{} in new code.
language: go
category: types
rule_id: USE-ANY
priority: info
tags:
- any
- interfaces
- google-style
---
Write any instead of interface{} in new code.

## Good

- func Print(v any)
- m := map[string]any{}

## Bad

- func Print(v interface{})
