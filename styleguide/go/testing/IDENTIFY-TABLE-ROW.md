---
type: Styleguide Rule
description: |-
  Do not identify a failing table row by its index. Print the inputs or a
  descriptive name, and use that name for the t.Run subtest.
language: go
category: testing
rule_id: IDENTIFY-TABLE-ROW
priority: warn
tags:
- testing
- table-driven
- failure-messages
- google-style
---
Do not identify a failing table row by its index. Print the inputs or a
descriptive name, and use that name for the t.Run subtest.

## Good

- t.Errorf("ToUpper(%q) = %q, want %q", d.input, got, d.want)

## Bad

- t.Errorf("Failed on case #%d", i)
