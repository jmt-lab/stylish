---
type: Styleguide Rule
description: |-
  Pass context.Context explicitly as the first parameter of functions that
  need it, including test helpers. Exceptions: HTTP handlers (req.Context()),
  streaming RPCs (stream.Context()), and tests (t.Context()).
language: go
category: concurrency
rule_id: CONTEXT-FIRST-PARAM
priority: warn
tags:
- context
- parameters
- google-style
---
Pass context.Context explicitly as the first parameter of functions that
need it, including test helpers. Exceptions: HTTP handlers (req.Context()),
streaming RPCs (stream.Context()), and tests (t.Context()).

## Good

- func F(ctx context.Context, id string) error
- func readTestFile(ctx context.Context, t *testing.T, path string) string

## Bad

- func F(id string, ctx context.Context) error
- func F(id string) error { ctx := context.Background(); ... } // drops caller's deadline
