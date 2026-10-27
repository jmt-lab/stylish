---
type: Styleguide Rule
description: |-
  Preallocate slice or map capacity only when the size is known or profiling
  justifies it, and comment the reason. Most code should let the runtime grow
  them; over-allocating wastes memory.
language: go
category: declarations
rule_id: SIZE-HINTS-WHEN-MEASURED
priority: hint
tags:
- performance
- allocation
- maps
- slices
- google-style
---
Preallocate slice or map capacity only when the size is known or profiling
justifies it, and comment the reason. Most code should let the runtime grow
them; over-allocating wastes memory.

## Good

- // Each shard processes shardSize (typically 32000+) elements.
seen := make(map[string]bool, shardSize)
- out := make([]string, 0, len(m)) // final size known

## Bad

- q := make([]Node, 0, 1000000) // guessed, unmeasured
