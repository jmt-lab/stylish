---
type: Styleguide Rule
description: |-
  Group imports in this order, separated by blank lines: standard library,
  other (project and third-party) packages, protocol buffer imports, and side-
  effect (blank) imports.
language: go
category: imports
rule_id: IMPORT-GROUPING
priority: warn
tags:
- imports
- organization
- google-style
---
Group imports in this order, separated by blank lines: standard library,
other (project and third-party) packages, protocol buffer imports, and side-
effect (blank) imports.

## Good

- import (
    "fmt"
    "os"

    "golang.org/x/text/encoding"

    foopb "myproj/foo/proto/proto"

    _ "myproj/rpc/protocols/dial"
)

## Bad

- import (
    "golang.org/x/text/encoding"
    "fmt"
    _ "myproj/rpc/protocols/dial"
    "os"
)
