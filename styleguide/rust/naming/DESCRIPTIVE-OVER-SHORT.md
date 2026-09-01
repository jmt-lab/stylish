---
type: Styleguide Rule
description: |-
  Carmack principle: Variable and function names should be descriptive
  and self-documenting. Clarity is more important than brevity.
language: rust
category: naming
rule_id: DESCRIPTIVE-OVER-SHORT
priority: warn
tags:
- naming
- carmack
- readability
---
Carmack principle: Variable and function names should be descriptive
and self-documenting. Clarity is more important than brevity.

## Good

- let entity_count = entities.len();
- let frame_delta_time = current - last;
- fn compute_visible_entities() {}

## Bad

- let cnt = entities.len();
- let dt = current - last;
- fn calc() {}
