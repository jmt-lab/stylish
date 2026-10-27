---
type: Styleguide Rule
description: |-
  Omit the type or type-like words from variable names; the compiler and usage
  already convey them. Add a qualifier only when two forms of the same value
  are in scope (raw vs parsed).
language: go
category: naming
rule_id: NO-TYPE-IN-VARIABLE-NAMES
priority: warn
tags:
- variables
- repetition
- google-style
---
Omit the type or type-like words from variable names; the compiler and usage
already convey them. Add a qualifier only when two forms of the same value
are in scope (raw vs parsed).

## Good

- var users int
- var name string
- var primary *Project
- limitRaw := r.FormValue("limit")
limit, err := strconv.Atoi(limitRaw)

## Bad

- var numUsers int
- var nameString string
- var userSlice []User
