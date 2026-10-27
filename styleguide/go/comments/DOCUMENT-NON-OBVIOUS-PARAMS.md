---
type: Styleguide Rule
description: |-
  Do not enumerate every parameter or field in docs. Document the error-prone
  or non-obvious ones and explain why they matter.
language: go
category: comments
rule_id: DOCUMENT-NON-OBVIOUS-PARAMS
priority: info
tags:
- documentation
- parameters
- google-style
---
Do not enumerate every parameter or field in docs. Document the error-prone
or non-obvious ones and explain why they matter.

## Good

- // Sprintf formats according to a format specifier and returns the resulting string.
//
// If data does not match the format verbs, warnings about the formatting
// errors are inlined into the output string.
func Sprintf(format string, data ...any) string

## Bad

- // Sprintf formats according to a format specifier and returns the resulting string.
//
// format is the format, and data is the interpolation data.
func Sprintf(format string, data ...any) string
