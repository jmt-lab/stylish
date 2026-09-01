---
type: Styleguide Rule
description: |-
  Functions should have banner-style block comments with consistent
  delimiter width. Include function name and purpose.
language: language-agnostic
category: comments
rule_id: BANNER-FUNCTION-DOCS
priority: warn
tags:
- documentation
- functions
- style
---
Functions should have banner-style block comments with consistent
delimiter width. Include function name and purpose.

## Good

- /*
================
FormatNumber

Formats a number with
thousand separators.
================
*/

## Bad

- // FormatNumber - formats numbers
- /* Quick comment */
