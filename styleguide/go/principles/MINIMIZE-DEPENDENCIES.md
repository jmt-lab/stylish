---
type: Styleguide Rule
description: |-
  Minimize explicit and implicit dependencies, avoid relying on undocumented
  behavior, and do not build unused features. Choose abstractions that fit the
  problem and make APIs able to grow gracefully.
language: go
category: principles
rule_id: MINIMIZE-DEPENDENCIES
priority: info
tags:
- maintainability
- dependencies
- coupling
- google-style
---
Minimize explicit and implicit dependencies, avoid relying on undocumented
behavior, and do not build unused features. Choose abstractions that fit the
problem and make APIs able to grow gracefully.

## Good

- import "strings" // the standard library covers the need

## Bad

- import "github.com/some/stringutils" // one function used, available in strings
- // parses the undocumented format of another package's Error() text
