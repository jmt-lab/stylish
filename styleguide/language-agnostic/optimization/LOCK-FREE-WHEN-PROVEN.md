---
type: Styleguide Rule
description: |-
  Lock-free data structures are complex and easy to get wrong. Use
  simple locks unless profiling shows lock contention is a real issue.
language: language-agnostic
category: optimization
rule_id: LOCK-FREE-WHEN-PROVEN
priority: warn
tags:
- concurrency
- locks
- complexity
---
Lock-free data structures are complex and easy to get wrong. Use
simple locks unless profiling shows lock contention is a real issue.

## Good

- // Simple mutex, measured overhead is acceptable

## Bad

- // Complex lock-free structure (no contention measured)
