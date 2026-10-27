---
type: Styleguide Rule
description: |-
  Import packages for side effects (import _) only in main packages or tests
  that need them, not in libraries. Exceptions are embed with //go:embed and
  bypassing static import checkers.
language: go
category: imports
rule_id: BLANK-IMPORTS-MAIN-ONLY
priority: warn
tags:
- imports
- side-effects
- dependencies
- google-style
---
Import packages for side effects (import _) only in main packages or tests
that need them, not in libraries. Exceptions are embed with //go:embed and
bypassing static import checkers.

## Good

- // cmd/server/main.go
package main

import _ "time/tzdata"
- import _ "embed" // file uses //go:embed

## Bad

- // library package
package imageutil

import _ "image/jpeg" // forces the dependency on every user
