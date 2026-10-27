---
type: Styleguide Rule
description: |-
  Be careful with := inside a new block: it declares a new variable that
  shadows the outer one, and the outer value is used after the block. Declare
  the extra variables with var and use = when you mean to update the outer
  variable.
language: go
category: naming
rule_id: AVOID-ACCIDENTAL-SHADOWING
priority: info
tags:
- shadowing
- variables
- scope
- google-style
---
Be careful with := inside a new block: it declares a new variable that
shadows the outer one, and the outer value is used after the block. Declare
the extra variables with var and use = when you mean to update the outer
variable.

## Good

- if *shortenDeadlines {
    var cancel func()
    ctx, cancel = context.WithTimeout(ctx, 3*time.Second)
    defer cancel()
}
- ctx, cancel := context.WithTimeout(ctx, 3*time.Second) // same scope: intentional stomp

## Bad

- if *shortenDeadlines {
    ctx, cancel := context.WithTimeout(ctx, 3*time.Second) // shadows ctx
    defer cancel()
}
// BUG: ctx here is still the caller's context
