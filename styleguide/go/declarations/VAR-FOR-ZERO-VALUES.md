---
type: Styleguide Rule
description: |-
  Declare with var when you want an empty zero value ready for later use
  (including unmarshal targets), not with explicit zero composite literals.
  Use new(T) or &T{} for pointers to zero values.
language: go
category: declarations
rule_id: VAR-FOR-ZERO-VALUES
priority: info
tags:
- variables
- zero-values
- google-style
---
Declare with var when you want an empty zero value ready for later use
(including unmarshal targets), not with explicit zero composite literals.
Use new(T) or &T{} for pointers to zero values.

## Good

- var (
    coords Point
    magic  [4]byte
    primes []int
)
- var coords Point
if err := json.Unmarshal(data, &coords); err != nil {}
- msg := new(pb.Bar)

## Bad

- var (
    coords = Point{X: 0, Y: 0}
    magic  = [4]byte{0, 0, 0, 0}
    primes = []int(nil)
)
