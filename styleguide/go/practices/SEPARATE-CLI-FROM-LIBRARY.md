---
type: Styleguide Rule
description: |-
  If code serves as both a library and a binary, keep the CLI separate so it
  is just another client of the library. Prefer a simple subcommand library
  unless you need more features; subcommands need not live in separate
  packages.
language: go
category: practices
rule_id: SEPARATE-CLI-FROM-LIBRARY
priority: info
tags:
- cli
- packages
- google-style
---
If code serves as both a library and a binary, keep the CLI separate so it
is just another client of the library. Prefer a simple subcommand library
unless you need more features; subcommands need not live in separate
packages.

## Good

- // mytool/        library API
// mytool/cmd/mytool/main.go   flag parsing, calls mytool.Run(ctx, opts)

## Bad

- // business logic implemented inside cobra RunE closures in package main
