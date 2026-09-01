---
type: Styleguide Rule
description: |-
  Code should be easy to understand and reason about. Avoid clever
  tricks that make code hard to read.
language: rust
category: practices
rule_id: REDUCE-COGNITIVE-LOAD
priority: warn
tags:
- practices
- readability
- carmack
---
Code should be easy to understand and reason about. Avoid clever
tricks that make code hard to read.

## Good

- // Clear intent
if entity.is_valid() && entity.is_alive() { ... }

## Bad

- // Clever but obscure
if entity.0 & 0x8000 != 0 && entity.1 > 0 { ... }
