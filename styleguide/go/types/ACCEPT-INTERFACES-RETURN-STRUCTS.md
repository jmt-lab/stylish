---
type: Styleguide Rule
description: |-
  Accept interfaces as parameters and return concrete types so callers get the
  full API. Return an interface only for error, deliberate encapsulation,
  runtime selection among types (factory, strategy, chaining), or to break an
  import cycle.
language: go
category: types
rule_id: ACCEPT-INTERFACES-RETURN-STRUCTS
priority: warn
tags:
- interfaces
- api
- return-types
- google-style
---
Accept interfaces as parameters and return concrete types so callers get the
full API. Return an interface only for error, deliberate encapsulation,
runtime selection among types (factory, strategy, chaining), or to break an
import cycle.

## Good

- func NewScanner(r io.Reader) *Scanner
- func NewWriter(format string) io.Writer { // picks a type at runtime
    switch format {
    case "json":
        return &jsonWriter{}
    default:
        return &textWriter{}
    }
}

## Bad

- func NewScanner(r *os.File) Scanner // concrete in, interface out
