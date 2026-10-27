---
type: Styleguide Rule
description: |-
  Give subtests short, readable names that are easy to type in -run filters.
  Avoid spaces, slashes, and non-printing characters. Put long descriptions in
  a separate field and inputs in failure messages. Subtests must not depend on
  each other.
language: go
category: testing
rule_id: SUBTEST-NAMES
priority: info
tags:
- testing
- subtests
- naming
- google-style
---
Give subtests short, readable names that are easy to type in -run filters.
Avoid spaces, slashes, and non-printing characters. Put long descriptions in
a separate field and inputs in failure messages. Subtests must not depend on
each other.

## Good

- t.Run("hu=en_bug-1234", func(t *testing.T) { ... })
- t.Run("empty_input", func(t *testing.T) { ... })

## Bad

- t.Run("check that there is no mention of scratched records or hovercrafts", ...)
- t.Run("AM/PM confusion", ...) // slash breaks test filters
