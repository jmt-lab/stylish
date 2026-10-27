---
type: Styleguide Rule
description: |-
  Do not write assertion helpers that both check and fail the test. Keep
  validation and failure reporting in the Test function, or have shared checks
  return a value or error (or a cmp.Option) that the test reports.
language: go
category: testing
rule_id: NO-ASSERTION-HELPERS
priority: warn
tags:
- testing
- assertions
- helpers
- google-style
---
Do not write assertion helpers that both check and fail the test. Keep
validation and failure reporting in the Test function, or have shared checks
return a value or error (or a cmp.Option) that the test reports.

## Good

- func validatePost(p BlogPost) error { /* returns descriptive error */ }

if err := validatePost(got); err != nil {
    t.Errorf("AddPost() returned invalid post: %v", err)
}
- func polygonCmp() cmp.Option // composable, does not touch *testing.T

## Bad

- func assertStringEq(t *testing.T, name, got, want string) {
    if got != want {
        t.Fatalf("%s = %q, want %q", name, got, want) // stops early, loses context
    }
}
