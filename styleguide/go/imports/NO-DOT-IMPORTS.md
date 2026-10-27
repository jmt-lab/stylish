---
type: Styleguide Rule
description: |-
  Do not use import . ; it hides where identifiers come from.
language: go
category: imports
rule_id: NO-DOT-IMPORTS
priority: warn
tags:
- imports
- readability
- google-style
---
Do not use import . ; it hides where identifiers come from.

## Good

- import "foo"

var myThing = foo.Bar()

## Bad

- import . "foo"

var myThing = Bar() // where is Bar defined?
