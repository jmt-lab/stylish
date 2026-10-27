---
type: Styleguide Rule
description: |-
  Make a variable name's length proportional to its scope and inversely
  proportional to how often it is used. Short names suit a few lines; names
  that live across a page need more words. Do not drop letters just to save
  typing.
language: go
category: naming
rule_id: NAME-LENGTH-BY-SCOPE
priority: warn
tags:
- variables
- scope
- readability
- google-style
---
Make a variable name's length proportional to its scope and inversely
proportional to how often it is used. Short names suit a few lines; names
that live across a page need more words. Do not drop letters just to save
typing.

## Good

- for i, n := range nodes { total += n.Weight * i }
- var pendingReplicationTasks []*Task // package scope
- sandbox := newSandbox()

## Bad

- var t []*Task // package-scoped, meaning unclear
- sbx := newSandbox() // letters dropped
- for theCurrentNodeIndex := range nodes {} // tiny scope, overlong name
