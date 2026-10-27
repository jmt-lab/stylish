---
type: Styleguide Rule
description: |-
  Use composite literals when initial elements or fields are known, instead of
  building values field by field. Do not use empty composite literals where a
  zero-value declaration reads more cleanly.
language: go
category: declarations
rule_id: COMPOSITE-LITERALS-FOR-KNOWN-VALUES
priority: info
tags:
- literals
- initialization
- google-style
---
Use composite literals when initial elements or fields are known, instead of
building values field by field. Do not use empty composite literals where a
zero-value declaration reads more cleanly.

## Good

- primes := []int{2, 3, 5, 7, 11}
- captains := map[string]string{"Kirk": "James Tiberius", "Picard": "Jean-Luc"}

## Bad

- var primes []int
primes = append(primes, 2)
primes = append(primes, 3)
primes = append(primes, 5)
