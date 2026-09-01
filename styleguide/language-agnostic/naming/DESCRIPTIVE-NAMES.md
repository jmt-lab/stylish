---
type: Styleguide Rule
description: |-
  Variable and function names should be descriptive and self-documenting.
  Clarity is more important than brevity. Subsystem prefixes (R_, S_, CL_)
  are acceptable abbreviations for namespace scoping (see SUBSYSTEM-PREFIX).
  Avoid abbreviations in the descriptive portion of names.
language: language-agnostic
category: naming
rule_id: DESCRIPTIVE-NAMES
priority: warn
tags:
- variables
- readability
- clarity
---
Variable and function names should be descriptive and self-documenting.
Clarity is more important than brevity. Subsystem prefixes (R_, S_, CL_)
are acceptable abbreviations for namespace scoping (see SUBSYSTEM-PREFIX).
Avoid abbreviations in the descriptive portion of names.

## Good

- entityNumber
- frameNumber
- currentFrameIndex
- shadowVolume

## Bad

- idx // Too abbreviated
- n // Unclear meaning
- tmp // Lazy naming
