---
type: Styleguide Rule
description: |-
  Omit repeated element and key types in slice and map literals (gofmt -s does
  this). Spell them out only when an unusual complex type benefits from the
  reminder.
language: go
category: formatting
rule_id: OMIT-REPEATED-LITERAL-TYPES
priority: info
tags:
- literals
- repetition
- google-style
---
Omit repeated element and key types in slice and map literals (gofmt -s does
this). Spell them out only when an unusual complex type benefits from the
reminder.

## Good

- good := []*Type{
    {A: 42},
    {A: 43},
}
- good := map[Type1]*Type2{
    {A: 1}: {B: 2},
}

## Bad

- repetitive := []*Type{
    &Type{A: 42},
    &Type{A: 43},
}
- repetitive := map[Type1]*Type2{
    Type1{A: 1}: &Type2{B: 2},
}
