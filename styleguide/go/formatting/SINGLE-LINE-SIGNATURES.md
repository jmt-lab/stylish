---
type: Styleguide Rule
description: |-
  Keep function and method signatures on one line. Wrapped parameter lists
  line up with the body and cause indentation confusion; reduce the number of
  parameters instead, for example with an option struct.
language: go
category: formatting
rule_id: SINGLE-LINE-SIGNATURES
priority: warn
tags:
- functions
- indentation
- google-style
---
Keep function and method signatures on one line. Wrapped parameter lists
line up with the body and cause indentation confusion; reduce the number of
parameters instead, for example with an option struct.

## Good

- func (r *SomeType) SomeLongFunctionName(foo1, foo2, foo3 string, foo4, foo5, foo6 int) {
    foo7 := bar(foo1)
}

## Bad

- func (r *SomeType) SomeLongFunctionName(foo1, foo2, foo3 string,
    foo4, foo5, foo6 int) {
    foo7 := bar(foo1) // looks like part of the signature
}
