---
type: Styleguide Rule
description: |-
  Format string mismatches are the second most common issue. Use
  static analysis to catch printf-style format errors.
language: language-agnostic
category: static_analysis
rule_id: FORMAT-STRING-ERRORS
priority: error
tags:
- format-strings
- printf
- safety
---
Format string mismatches are the second most common issue. Use
static analysis to catch printf-style format errors.

## Good

- printf("%d", intValue); // Matches

## Bad

- printf("%s", intValue); // Analyzer catches mismatch
