---
type: Styleguide Rule
description: |-
  Document intended package usage with runnable Example functions in _test.go
  files so they appear in godoc and are verified by tests. Fall back to
  formatted code in comments only when a runnable example is infeasible.
language: go
category: comments
rule_id: RUNNABLE-EXAMPLES
priority: info
tags:
- documentation
- examples
- testing
- google-style
---
Document intended package usage with runnable Example functions in _test.go
files so they appear in godoc and are verified by tests. Fall back to
formatted code in comments only when a runnable example is infeasible.

## Good

- // config_test.go
func ExampleConfig_WriteTo() {
    cfg := &Config{Name: "example"}
    if err := cfg.WriteTo(os.Stdout); err != nil {
        log.Fatal(err)
    }
    // Output:
    // {"name": "example"}
}

## Bad

- // config.go (production source)
func ExampleConfig_WriteTo() {} // examples belong in test files
