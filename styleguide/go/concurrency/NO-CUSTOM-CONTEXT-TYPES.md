---
type: Styleguide Rule
description: |-
  Never define custom context types or use interfaces other than
  context.Context in signatures. Pass application data as parameters,
  receivers, or, only if it truly belongs there, as context values.
language: go
category: concurrency
rule_id: NO-CUSTOM-CONTEXT-TYPES
priority: error
tags:
- context
- types
- google-style
---
Never define custom context types or use interfaces other than
context.Context in signatures. Pass application data as parameters,
receivers, or, only if it truly belongs there, as context values.

## Good

- func Handle(ctx context.Context, user *User) error

## Bad

- type AppContext interface {
    context.Context
    User() *User
}
func Handle(ctx AppContext) error
