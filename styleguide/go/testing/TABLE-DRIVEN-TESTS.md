---
type: Styleguide Rule
description: |-
  Use table-driven tests when many cases share the same checking logic. When
  cases need different logic, write separate test functions (for example
  success vs error tables) instead of branching on row fields.
language: go
category: testing
rule_id: TABLE-DRIVEN-TESTS
priority: info
tags:
- testing
- table-driven
- google-style
---
Use table-driven tests when many cases share the same checking logic. When
cases need different logic, write separate test functions (for example
success vs error tables) instead of branching on row fields.

## Good

- tests := []struct {
    a, b string
    want int
}{
    {"", "", 0},
    {"a", "", 1},
}
for _, test := range tests {
    if got := Compare(test.a, test.b); got != test.want {
        t.Errorf("Compare(%q, %q) = %v, want %v", test.a, test.b, got, test.want)
    }
}

## Bad

- for _, test := range tests {
    switch test.codex { // row field selects setup and logic
    case fake:
        codex = newFakeCodex()
    case prod:
        codex = setupCodex(t)
    }
}
