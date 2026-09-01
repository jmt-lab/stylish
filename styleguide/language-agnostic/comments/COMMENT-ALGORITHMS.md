---
type: Styleguide Rule
description: |-
  Complex or non-obvious algorithms should be commented. Include
  references to papers or sources when applicable.
language: language-agnostic
category: comments
rule_id: COMMENT-ALGORITHMS
priority: warn
tags:
- algorithms
- documentation
- references
---
Complex or non-obvious algorithms should be commented. Include
references to papers or sources when applicable.

## Good

- // Fast inverse square root from Quake III
// See: https://...
- // Binary space partitioning as described in Foley & van Dam

## Bad

- // Math stuff
result = ComplexCalculation();
