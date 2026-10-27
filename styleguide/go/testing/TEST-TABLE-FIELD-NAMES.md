---
type: Styleguide Rule
description: |-
  Use field names in test-case struct literals when the table is long,
  adjacent fields share a type, or zero-value fields are omitted.
language: go
category: testing
rule_id: TEST-TABLE-FIELD-NAMES
priority: info
tags:
- testing
- table-driven
- literals
- google-style
---
Use field names in test-case struct literals when the table is long,
adjacent fields share a type, or zero-value fields are omitted.

## Good

- {
    slice:     []string{"a", "b", ""},
    separator: ",",
    skipEmpty: true,
    want:      "a,b",
},

## Bad

- {[]string{"a", "b", ""}, ",", true, "a,b"}, // which bool is which?
