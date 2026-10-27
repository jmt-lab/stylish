---
type: Styleguide Rule
description: |-
  Handle errors and other terminal conditions first and return early; keep the
  normal path unindented after the if block, not in an else. Move declarations
  out of the if-initializer when the variable is used for more than a few
  lines.
language: go
category: error_handling
rule_id: INDENT-ERROR-FLOW
priority: warn
tags:
- errors
- control-flow
- nesting
- google-style
---
Handle errors and other terminal conditions first and return early; keep the
normal path unindented after the if block, not in an else. Move declarations
out of the if-initializer when the variable is used for more than a few
lines.

## Good

- x, err := f()
if err != nil {
    return err
}
// lots of code that uses x

## Bad

- if x, err := f(); err != nil {
    return err
} else {
    // lots of code that uses x, needlessly indented
}
