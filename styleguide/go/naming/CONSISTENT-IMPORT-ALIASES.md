---
type: Styleguide Rule
description: |-
  When a package is renamed at import, the local name must follow package
  naming rules, and the same alias should be used across files in the same or
  nearby packages.
language: go
category: naming
rule_id: CONSISTENT-IMPORT-ALIASES
priority: info
tags:
- imports
- packages
- consistency
- google-style
---
When a package is renamed at import, the local name must follow package
naming rules, and the same alias should be used across files in the same or
nearby packages.

## Good

- import foopb "path/to/foo_go_proto" // same alias in every file

## Bad

- import foo_pb "path/to/foo_go_proto" // underscore in alias
- import fpb "path/to/foo_go_proto" // foopb used elsewhere in the package
