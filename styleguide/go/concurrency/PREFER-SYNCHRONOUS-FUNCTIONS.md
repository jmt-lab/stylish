---
type: Styleguide Rule
description: |-
  Prefer synchronous functions that return results directly and finish
  callbacks and channel work before returning. Callers can add concurrency
  with a goroutine, but cannot easily remove concurrency built into an API.
language: go
category: concurrency
rule_id: PREFER-SYNCHRONOUS-FUNCTIONS
priority: warn
tags:
- goroutines
- api
- testing
- google-style
---
Prefer synchronous functions that return results directly and finish
callbacks and channel work before returning. Callers can add concurrency
with a goroutine, but cannot easily remove concurrency built into an API.

## Good

- func Fetch(ctx context.Context, urls []string) ([]Page, error)

// caller opts in to concurrency
go func() { pages, err = Fetch(ctx, urls) }()

## Bad

- func Fetch(urls []string) <-chan Page // spawns goroutines; caller must drain and guess lifetime
