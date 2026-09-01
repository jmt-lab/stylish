---
type: Styleguide Rule
description: |-
  Variable and function names should be descriptive and self-documenting.
  Clarity over brevity. Aligns with Carmack's DESCRIPTIVE-NAMES.
language: typescript
category: naming
rule_id: TS-DESCRIPTIVE-NAMES
priority: warn
tags:
- variables
- functions
- clarity
---
Variable and function names should be descriptive and self-documenting.
Clarity over brevity. Aligns with Carmack's DESCRIPTIVE-NAMES.

## Good

- const entityNumber = 42;
- const frameTimestamp = Date.now();
- function calculateShadowVolume() {}

## Bad

- const idx = 42; // Too abbreviated
- const ts = Date.now(); // Unclear
- function calcSV() {} // Over-abbreviated
