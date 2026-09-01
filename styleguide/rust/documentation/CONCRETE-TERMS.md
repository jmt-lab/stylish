---
type: Styleguide Rule
description: Use concrete, measurable terms instead of qualitative judgments (e.g., 'processes 1GB/sec' not 'fast').
language: rust
category: documentation
rule_id: CONCRETE-TERMS
priority: error
tags:
- documentation
- precision
---
Use concrete, measurable terms instead of qualitative judgments (e.g., 'processes 1GB/sec' not 'fast').

## Good

- /// Allocates with 24 bytes overhead per entry.
- /// Completes in O(1) time.

## Bad

- /// Fast allocation.
- /// Efficient lookup.
