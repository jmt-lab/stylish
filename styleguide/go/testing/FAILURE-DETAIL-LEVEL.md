---
type: Styleguide Rule
description: |-
  Scale failure detail to the test. Identify which call failed in multi-step
  interactions, keep setup failures brief, use %q for strings and %+v for
  small structs, and trigger your failure path during development to check
  that the message helps.
language: go
category: testing
rule_id: FAILURE-DETAIL-LEVEL
priority: hint
tags:
- testing
- failure-messages
- formatting
- google-style
---
Scale failure detail to the test. Identify which call failed in multi-step
interactions, keep setup failures brief, use %q for strings and %+v for
small structs, and trigger your failure path during development to check
that the message helps.

## Good

- t.Fatalf("Setup: Failed to set up test database: %s", err)
- t.Errorf("second call: Lookup(%q) = %+v, want %+v", key, got, want)

## Bad

- t.Errorf("Lookup = %v", got) // which of the 3 calls? empty string invisible
