---
type: Styleguide Rule
description: |-
  Use cmp.Equal and cmp.Diff (with protocmp.Transform for protos) for complex
  comparisons in tests. Do not use reflect.DeepEqual, which depends on
  unexported fields and implementation details, and do not use cmp in
  production code since it may panic.
language: go
category: testing
rule_id: USE-CMP-NOT-DEEPEQUAL
priority: warn
tags:
- testing
- comparison
- cmp
- google-style
---
Use cmp.Equal and cmp.Diff (with protocmp.Transform for protos) for complex
comparisons in tests. Do not use reflect.DeepEqual, which depends on
unexported fields and implementation details, and do not use cmp in
production code since it may panic.

## Good

- if diff := cmp.Diff(want, got, protocmp.Transform()); diff != "" {
    t.Errorf("Foo() mismatch (-want +got):\n%s", diff)
}

## Bad

- if !reflect.DeepEqual(got, want) {
    t.Errorf("Foo() = %v, want %v", got, want)
}
