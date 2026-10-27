---
type: Styleguide Rule
description: |-
  Use backtick raw string literals for constant multi-line strings instead of
  concatenating quoted strings with \n.
language: go
category: declarations
rule_id: RAW-STRINGS-FOR-MULTILINE
priority: info
tags:
- strings
- literals
- google-style
---
Use backtick raw string literals for constant multi-line strings instead of
concatenating quoted strings with \n.

## Good

- usage := `Usage:

custom_tool [args]`

## Bad

- usage := "" +
    "Usage:\n" +
    "\n" +
    "custom_tool [args]"
