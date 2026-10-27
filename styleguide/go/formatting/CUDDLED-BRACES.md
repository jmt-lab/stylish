---
type: Styleguide Rule
description: |-
  Cuddle braces in slice and array literals (}, {) only when indentation still
  matches and every inner value is a literal or proto builder, not a variable
  or expression.
language: go
category: formatting
rule_id: CUDDLED-BRACES
priority: info
tags:
- literals
- braces
- google-style
---
Cuddle braces in slice and array literals (}, {) only when indentation still
matches and every inner value is a literal or proto builder, not a variable
or expression.

## Good

- good := []*Type{{
    Field: "value",
}, {
    Field: "value",
}}
- good := []*Type{
    first, // cannot be cuddled
    {Field: "second"},
}

## Bad

- bad := []*Type{
    first,
    {
        Field: "second",
    }}
