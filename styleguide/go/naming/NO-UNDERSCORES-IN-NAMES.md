---
type: Styleguide Rule
description: |-
  Go identifiers should not contain underscores. Exceptions: packages imported
  only by generated code, Test/Benchmark/Example functions in _test.go files,
  and low-level OS/cgo interop. Filenames may contain underscores.
language: go
category: naming
rule_id: NO-UNDERSCORES-IN-NAMES
priority: warn
tags:
- identifiers
- underscores
- google-style
---
Go identifiers should not contain underscores. Exceptions: packages imported
only by generated code, Test/Benchmark/Example functions in _test.go files,
and low-level OS/cgo interop. Filenames may contain underscores.

## Good

- func TestParse_EmptyInput(t *testing.T) // allowed in *_test.go
- userID := req.UserID

## Bad

- user_id := req.UserID
- func load_config() error
