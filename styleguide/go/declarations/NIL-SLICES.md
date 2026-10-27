---
type: Styleguide Rule
description: |-
  Declare empty local slices as nil (var s []T) rather than []T{}. Do not
  design APIs that distinguish nil from empty slices; check emptiness with
  len(s) == 0.
language: go
category: declarations
rule_id: NIL-SLICES
priority: warn
tags:
- slices
- nil
- api
- google-style
---
Declare empty local slices as nil (var s []T) rather than []T{}. Do not
design APIs that distinguish nil from empty slices; check emptiness with
len(s) == 0.

## Good

- var t []string
- if len(s) == 0 {
    return
}

## Bad

- t := []string{}
- if s == nil { // empty non-nil slices slip through
    return
}
- // Returns nil on system error, empty if the input was empty.
func Ping(hosts []string) []string
