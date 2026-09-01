---
type: Styleguide Rule
description: |-
  Memory allocation is expensive. Pre-allocate or use stack allocation
  for performance-critical code executed every frame.
language: language-agnostic
category: optimization
rule_id: AVOID-ALLOCATIONS-HOT-PATH
priority: warn
tags:
- allocation
- hot-path
- performance
---
Memory allocation is expensive. Pre-allocate or use stack allocation
for performance-critical code executed every frame.

## Good

- // Pre-allocated buffer reused each frame
static char buffer[4096];

## Bad

- // Allocate every frame
char* buffer = malloc(4096);
