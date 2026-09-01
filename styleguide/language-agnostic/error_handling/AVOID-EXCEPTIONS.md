---
type: Styleguide Rule
description: |-
  Exceptions should be reserved for truly exceptional circumstances.
  Prefer explicit error returns for expected failure cases.
language: language-agnostic
category: error_handling
rule_id: AVOID-EXCEPTIONS
priority: error
tags:
- exceptions
- control-flow
- performance
---
Exceptions should be reserved for truly exceptional circumstances.
Prefer explicit error returns for expected failure cases.

## Good

- Result<Data> LoadFile(path) // Explicit error return
- bool TryConnect(address) // Boolean success

## Bad

- Data LoadFile(path) // Throws on any error
