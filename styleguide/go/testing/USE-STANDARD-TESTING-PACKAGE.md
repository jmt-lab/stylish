---
type: Styleguide Rule
description: |-
  Write tests with the standard testing package plus cmp for comparisons. Do
  not use third-party testing frameworks or assertion libraries.
language: go
category: testing
rule_id: USE-STANDARD-TESTING-PACKAGE
priority: warn
tags:
- testing
- frameworks
- google-style
---
Write tests with the standard testing package plus cmp for comparisons. Do
not use third-party testing frameworks or assertion libraries.

## Good

- func TestParse(t *testing.T) {
    got, err := Parse(in)
    if err != nil {
        t.Fatalf("Parse(%q) failed: %v", in, err)
    }
    if diff := cmp.Diff(want, got); diff != "" {
        t.Errorf("Parse(%q) mismatch (-want +got):\n%s", in, diff)
    }
}

## Bad

- assert.Equal(t, want, got)
- Expect(got).To(Equal(want)) // BDD framework
