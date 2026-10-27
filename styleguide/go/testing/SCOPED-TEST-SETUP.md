---
type: Styleguide Rule
description: |-
  Scope setup to the tests that need it by calling helpers explicitly, not
  from init or package-level state. Use sync.Once to amortize expensive setup
  without teardown, and TestMain only when every test needs shared setup with
  teardown. Reset any global state a test changes.
language: go
category: testing
rule_id: SCOPED-TEST-SETUP
priority: info
tags:
- testing
- setup
- hermeticity
- google-style
---
Scope setup to the tests that need it by calling helpers explicitly, not
from init or package-level state. Use sync.Once to amortize expensive setup
without teardown, and TestMain only when every test needs shared setup with
teardown. Reset any global state a test changes.

## Good

- func TestParseData(t *testing.T) {
    data := mustLoadDataset(t)
    // ...
}

## Bad

- var dataset []byte

func init() {
    dataset = mustLoadDataset() // every test, even unrelated ones, pays the cost
}
