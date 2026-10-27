---
type: Styleguide Rule
description: |-
  Use MixedCaps or mixedCaps for multi-word names, never underscores. This
  applies even to constants: exported names start uppercase, unexported
  (including locals) start lowercase.
language: go
category: naming
rule_id: MIXEDCAPS-NAMES
priority: error
tags:
- mixedcaps
- identifiers
- google-style
---
Use MixedCaps or mixedCaps for multi-word names, never underscores. This
applies even to constants: exported names start uppercase, unexported
(including locals) start lowercase.

## Good

- const MaxLength = 64
- maxLength := 64
- func parseHeader(raw []byte) (*Header, error)

## Bad

- const MAX_LENGTH = 64 // SCREAMING_SNAKE is not Go style
- max_length := 64 // snake_case
- func Parse_Header(raw []byte) (*Header, error)
