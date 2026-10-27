---
type: Styleguide Rule
description: |-
  Express ideas with the most standard tool that suffices: core language
  constructs first (slices, maps, channels, structs, loops), then the standard
  library, and only then a new dependency or custom machinery. Complexity is
  easy to add and hard to remove.
language: go
category: principles
rule_id: LEAST-MECHANISM
priority: warn
tags:
- simplicity
- dependencies
- google-style
---
Express ideas with the most standard tool that suffices: core language
constructs first (slices, maps, channels, structs, loops), then the standard
library, and only then a new dependency or custom machinery. Complexity is
easy to add and hard to remove.

## Good

- seen := map[string]bool{}
if seen[key] { continue }
- *flagTimeout = 5 * time.Second // override bound flag value in a test

## Bad

- s := sets.NewStringSet() // third-party set for a simple membership check
- flag.Set("timeout", "5s") // heavier than assigning the variable
