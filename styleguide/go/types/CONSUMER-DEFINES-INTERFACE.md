---
type: Styleguide Rule
description: |-
  Define interfaces in the package that consumes them, with only the methods
  that package uses, and keep them unexported if only used internally.
  Producers export an interface only when the interface is the product
  (io.Writer, hash.Hash, generated protocols).
language: go
category: types
rule_id: CONSUMER-DEFINES-INTERFACE
priority: warn
tags:
- interfaces
- packages
- api
- google-style
---
Define interfaces in the package that consumes them, with only the methods
that package uses, and keep them unexported if only used internally.
Producers export an interface only when the interface is the product
(io.Writer, hash.Hash, generated protocols).

## Good

- package report

type rowSource interface { // only what report needs
    Next() (Row, bool)
}

func Render(src rowSource) string

## Bad

- package storage

type Storage interface { // producer-defined, 20 methods "for clients"
    Get(); Put(); Delete(); List(); // ...
}
func New() Storage
