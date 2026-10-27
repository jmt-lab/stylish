---
type: Styleguide Rule
description: |-
  Do not insert artificial line breaks into for clauses. Move secondary
  conditions into the body with break, or let the line be long.
language: go
category: control_flow
rule_id: SINGLE-LINE-FOR
priority: info
tags:
- loops
- indentation
- google-style
---
Do not insert artificial line breaks into for clauses. Move secondary
conditions into the body with break, or let the line be long.

## Good

- for i, max := 0, collection.Size(); i < max; i++ {
    if collection.HasPendingWriters() {
        break
    }
}

## Bad

- for i, max := 0, collection.Size(); i < max &&
    !collection.HasPendingWriters(); i++ {
}
