---
type: Styleguide Rule
description: |-
  Do not compare output whose exact form is owned by another package, such as
  json.Marshal bytes or formatted strings. Parse it and compare semantically
  relevant values.
language: go
category: testing
rule_id: COMPARE-STABLE-RESULTS
priority: info
tags:
- testing
- brittleness
- serialization
- google-style
---
Do not compare output whose exact form is owned by another package, such as
json.Marshal bytes or formatted strings. Parse it and compare semantically
relevant values.

## Good

- var got map[string]any
if err := json.Unmarshal(out, &got); err != nil { t.Fatal(err) }
if diff := cmp.Diff(want, got); diff != "" { t.Errorf(...) }

## Bad

- if string(out) != `{"a":1,"b":2}` { // breaks if encoding/json changes spacing or order
    t.Errorf(...)
}
