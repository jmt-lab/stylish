---
type: Styleguide Rule
description: |-
  When comparing a variable with a constant, put the variable on the left.
language: go
category: control_flow
rule_id: NO-YODA-CONDITIONS
priority: warn
tags:
- conditionals
- readability
- google-style
---
When comparing a variable with a constant, put the variable on the left.

## Good

- if result == "foo" {}

## Bad

- if "foo" == result {}
