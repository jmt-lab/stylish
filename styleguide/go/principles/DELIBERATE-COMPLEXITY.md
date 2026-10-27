---
type: Styleguide Rule
description: |-
  Keep code simple and readable top to bottom without clever tricks or
  needless abstraction. When complexity is warranted (performance, many
  clients), add it deliberately with comments, tests, and examples that
  explain it.
language: go
category: principles
rule_id: DELIBERATE-COMPLEXITY
priority: info
tags:
- simplicity
- maintainability
- google-style
---
Keep code simple and readable top to bottom without clever tricks or
needless abstraction. When complexity is warranted (performance, many
clients), add it deliberately with comments, tests, and examples that
explain it.

## Good

- // Hand-unrolled loop: 3x faster in BenchmarkChecksum; keep in sync with checksumSlow.
for i := 0; i+4 <= len(b); i += 4 { ... }

## Bad

- // generic pipeline framework introduced to transform a single slice
p := pipeline.New[Item]().Map(f).Filter(g).Collect()
