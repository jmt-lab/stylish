---
type: Styleguide Rule
description: |-
  Use := to declare and initialize a variable with a non-zero value.
language: go
category: declarations
rule_id: SHORT-DECL-FOR-NONZERO
priority: info
tags:
- variables
- initialization
- google-style
---
Use := to declare and initialize a variable with a non-zero value.

## Good

- i := 42
- name := user.Name()

## Bad

- var i = 42
