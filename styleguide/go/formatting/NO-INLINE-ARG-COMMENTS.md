---
type: Styleguide Rule
description: |-
  Avoid inline comments that label individual call arguments; use an option
  struct or better documentation. Break call lines only by semantic grouping,
  when it aids understanding, not to fit a width.
language: go
category: formatting
rule_id: NO-INLINE-ARG-COMMENTS
priority: info
tags:
- functions
- arguments
- options
- google-style
---
Avoid inline comments that label individual call arguments; use an option
struct or better documentation. Break call lines only by semantic grouping,
when it aids understanding, not to fit a width.

## Good

- srv := server.New(ctx, server.Options{Port: 42})
- canvas.RenderHeptagon(fillColor,
    x0, y0, vertexColor0,
    x1, y1, vertexColor1,
    x2, y2, vertexColor2,
)

## Bad

- srv := server.New(
    ctx,
    42, // Port
)
