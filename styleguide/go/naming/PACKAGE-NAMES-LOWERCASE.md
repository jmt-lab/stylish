---
type: Styleguide Rule
description: |-
  Package names must be short, lowercase letters and digits only, with multi-
  word names left unbroken. Rename packages with underscores (e.g. generated
  code) to a valid Go name when importing.
language: go
category: naming
rule_id: PACKAGE-NAMES-LOWERCASE
priority: warn
tags:
- packages
- identifiers
- google-style
---
Package names must be short, lowercase letters and digits only, with multi-
word names left unbroken. Rename packages with underscores (e.g. generated
code) to a valid Go name when importing.

## Good

- package tabwriter
- package oauth2
- import foopb "path/to/foo_go_proto"

## Bad

- package tabWriter // mixed case
- package tab_writer // underscore
- import "path/to/foo_go_proto" // used as foo_go_proto.Message
