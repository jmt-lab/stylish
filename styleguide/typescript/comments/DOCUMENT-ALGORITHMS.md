---
type: Styleguide Rule
description: |-
  Complex algorithms should be commented with references to sources,
  papers, or explanations of the approach.
language: typescript
category: comments
rule_id: DOCUMENT-ALGORITHMS
priority: warn
tags:
- algorithms
- documentation
- references
---
Complex algorithms should be commented with references to sources,
papers, or explanations of the approach.

## Good

- // Binary search with interpolation for better average case // See: https://en.wikipedia.org/wiki/Interpolation_search
- // Fast inverse square root adapted from Quake III

## Bad

- // Complex math const result = algorithm(data);
