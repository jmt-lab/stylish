---
type: Styleguide Rule
description: |-
  Interfaces should not use I prefix. This is outdated Hungarian notation.
  Per ts.dev/style, interfaces and classes share the same namespace.
language: typescript
category: naming
rule_id: TS-NO-I-PREFIX
priority: warn
tags:
- interfaces
- antipattern
---
Interfaces should not use I prefix. This is outdated Hungarian notation.
Per ts.dev/style, interfaces and classes share the same namespace.

## Good

- interface Entity {}
- interface Renderable {}

## Bad

- interface IEntity {} // I prefix
- interface IRenderable {} // I prefix
