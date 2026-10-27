---
type: Styleguide Rule
description: |-
  Panic only for API misuse (like the standard library) or as an internal
  mechanism with a matching recover that turns it into an error at the package
  boundary. Such panics must never escape the package, and recover must re-
  panic values it does not own.
language: go
category: error_handling
rule_id: PANIC-NOT-ACROSS-PACKAGES
priority: info
tags:
- panic
- recover
- api
- google-style
---
Panic only for API misuse (like the standard library) or as an internal
mechanism with a matching recover that turns it into an error at the package
boundary. Such panics must never escape the package, and recover must re-
panic values it does not own.

## Good

- func Parse(in string) (_ *Node, err error) {
    defer func() {
        if p := recover(); p != nil {
            sErr, ok := p.(*syntaxError)
            if !ok {
                panic(p) // not ours
            }
            err = fmt.Errorf("syntax error: %v", sErr.msg)
        }
    }()
    // ...
}

## Bad

- func Parse(in string) *Node {
    panic(&syntaxError{"bad int"}) // escapes into caller's package
}
