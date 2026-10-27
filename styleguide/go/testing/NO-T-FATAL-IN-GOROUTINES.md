---
type: Styleguide Rule
description: |-
  Never call t.Fatal, t.FailNow, or similar from goroutines other than the one
  running the test or subtest. Use t.Error and return.
language: go
category: testing
rule_id: NO-T-FATAL-IN-GOROUTINES
priority: error
tags:
- testing
- goroutines
- t-fatal
- google-style
---
Never call t.Fatal, t.FailNow, or similar from goroutines other than the one
running the test or subtest. Use t.Error and return.

## Good

- go func() {
    defer wg.Done()
    if err := engine.Vroom(); err != nil {
        t.Errorf("No vroom left on engine: %v", err)
        return
    }
}()

## Bad

- go func() {
    if err := engine.Vroom(); err != nil {
        t.Fatalf("No vroom: %v", err) // invalid from a spawned goroutine
    }
}()
