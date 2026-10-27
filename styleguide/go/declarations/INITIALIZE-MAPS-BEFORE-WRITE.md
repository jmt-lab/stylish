---
type: Styleguide Rule
description: |-
  Initialize maps with make or a literal before writing to them; writing to a
  nil map panics. Reading a nil map is fine.
language: go
category: declarations
rule_id: INITIALIZE-MAPS-BEFORE-WRITE
priority: error
tags:
- maps
- nil
- zero-values
- google-style
---
Initialize maps with make or a literal before writing to them; writing to a
nil map panics. Reading a nil map is fine.

## Good

- counts := make(map[string]int)
counts["a"]++

## Bad

- var counts map[string]int
counts["a"]++ // panic: assignment to entry in nil map
