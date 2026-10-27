---
type: Styleguide Rule
description: |-
  Put the closing brace of a multi-line literal on its own line at the opening
  brace's indentation, ending the last element with a comma.
language: go
category: formatting
rule_id: MATCHING-BRACES
priority: warn
tags:
- literals
- braces
- google-style
---
Put the closing brace of a multi-line literal on its own line at the opening
brace's indentation, ending the last element with a comma.

## Good

- good := []*Type{{Key: "value"}}
- good := []*Type{
    {Key: "multi"},
    {Key: "line"},
}

## Bad

- bad := []*Type{
    {Key: "multi"},
    {Key: "line"}}
- bad := []*Type{
    {
        Key: "value"},
}
