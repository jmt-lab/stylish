---
type: Styleguide Rule
description: |-
  Compare structs, slices, and maps whole against a constructed expected value
  with a deep comparison, not field by field. Compare multiple return values
  individually; do not wrap them in a struct.
language: go
category: testing
rule_id: COMPARE-FULL-STRUCTURES
priority: info
tags:
- testing
- comparison
- cmp
- google-style
---
Compare structs, slices, and maps whole against a constructed expected value
with a deep comparison, not field by field. Compare multiple return values
individually; do not wrap them in a struct.

## Good

- want := &Doc{Type: "blogPost", Comments: 2, Authors: []string{"isaac", "emmy"}}
if !cmp.Equal(got, want) {
    t.Errorf("AddPost() = %+v, want %+v", got, want)
}

## Bad

- if got.Type != "blogPost" { t.Errorf(...) }
if got.Comments != 2 { t.Errorf(...) }
if len(got.Authors) != 2 { t.Errorf(...) }
