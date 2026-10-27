---
type: Styleguide Rule
description: |-
  Package-level state is acceptable only if it is logically constant, its
  observable behavior is stateless (such as an invisible cache), it does not
  leak outside the process, and no predictable behavior is expected. It is
  unsafe when independent code or tests interact through it, users want to
  swap it for test doubles, or it depends on init order.
language: go
category: practices
rule_id: GLOBAL-STATE-LITMUS-TEST
priority: info
tags:
- global-state
- testing
- google-style
---
Package-level state is acceptable only if it is logically constant, its
observable behavior is stateless (such as an invisible cache), it does not
leak outside the process, and no predictable behavior is expected. It is
unsafe when independent code or tests interact through it, users want to
swap it for test doubles, or it depends on init order.

## Good

- var crcTable = crc32.MakeTable(crc32.Castagnoli) // logically constant
- var cache sync.Map // private memoization, indistinguishable to callers

## Bad

- var Sinks []Sink // "set at init and never thereafter"; tests swap it
- func OnUnhealthy(f func()) { unhealthyFuncs = append(unhealthyFuncs, f) }
