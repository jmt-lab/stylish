---
type: Styleguide Rule
description: |-
  For large values print a diff instead of both values, put it after a
  newline, and state its direction, e.g. (-want +got) when calling
  cmp.Diff(want, got).
language: go
category: testing
rule_id: PRINT-DIFFS-WITH-DIRECTION
priority: info
tags:
- testing
- diffs
- failure-messages
- google-style
---
For large values print a diff instead of both values, put it after a
newline, and state its direction, e.g. (-want +got) when calling
cmp.Diff(want, got).

## Good

- if diff := cmp.Diff(want, got); diff != "" {
    t.Errorf("Parse(%q) returned unexpected diff (-want +got):\n%s", in, diff)
}

## Bad

- t.Errorf("Parse(%q) = %v, want %v", in, hugeGot, hugeWant) // unreadable
- t.Errorf("diff: %s", cmp.Diff(want, got)) // no direction key, no newline
