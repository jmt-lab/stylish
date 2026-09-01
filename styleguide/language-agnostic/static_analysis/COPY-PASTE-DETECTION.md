---
type: Styleguide Rule
description: |-
  Carmack was surprised how often copy-paste-modify resulted in bugs.
  Use static analysis to find suspicious duplicated code.
language: language-agnostic
category: static_analysis
rule_id: COPY-PASTE-DETECTION
priority: warn
tags:
- copy-paste
- duplication
- bugs
---
Carmack was surprised how often copy-paste-modify resulted in bugs.
Use static analysis to find suspicious duplicated code.

## Good

- # Analyzer finds:
# entity1->x = value;
# entity1->y = value; // Should be entity2?

## Bad

- # Copy-paste bug undetected
