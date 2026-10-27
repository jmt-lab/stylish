---
type: Styleguide Rule
description: |-
  Use generics only when they meet a real requirement. If only one type is
  instantiated, write concrete code first; prefer a shared interface when one
  exists. Do not build DSLs, error-handling frameworks, or assertion libraries
  with generics. Document exported generic APIs with runnable examples.
language: go
category: types
rule_id: GENERICS-WHEN-NEEDED
priority: warn
tags:
- generics
- simplicity
- google-style
---
Use generics only when they meet a real requirement. If only one type is
instantiated, write concrete code first; prefer a shared interface when one
exists. Do not build DSLs, error-handling frameworks, or assertion libraries
with generics. Document exported generic APIs with runnable examples.

## Good

- func SumInts(xs []int) int // only ints are used today
- func Map[T, U any](xs []T, f func(T) U) []U // used with many types

## Bad

- type Result[T any] struct{ val T; err error } // custom error-handling framework
func (r Result[T]) Then(f func(T) Result[T]) Result[T]
- func Process[T any](x T) {} // only ever called with *Order
