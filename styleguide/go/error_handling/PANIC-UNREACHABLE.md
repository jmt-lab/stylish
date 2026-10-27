---
type: Styleguide Rule
description: |-
  Use panic("unreachable") after calls that never return (such as log.Fatal)
  when the compiler needs a terminating statement.
language: go
category: error_handling
rule_id: PANIC-UNREACHABLE
priority: hint
tags:
- panic
- control-flow
- google-style
---
Use panic("unreachable") after calls that never return (such as log.Fatal)
when the compiler needs a terminating statement.

## Good

- default:
    log.Fatalf("Sorry, %d is not the answer.", i)
    panic("unreachable")

## Bad

- default:
    log.Fatalf("Sorry, %d is not the answer.", i)
    return "" // misleading dead return
