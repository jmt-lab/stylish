---
type: Styleguide Rule
description: |-
  Do not store a context.Context in a struct field. Pass ctx as a parameter to
  each method that needs it, unless an external interface's signature forces
  otherwise.
language: go
category: concurrency
rule_id: NO-CONTEXT-IN-STRUCTS
priority: warn
tags:
- context
- structs
- google-style
---
Do not store a context.Context in a struct field. Pass ctx as a parameter to
each method that needs it, unless an external interface's signature forces
otherwise.

## Good

- type Client struct{ conn *grpc.ClientConn }

func (c *Client) Get(ctx context.Context, key string) ([]byte, error)

## Bad

- type Client struct {
    ctx  context.Context // ambient, lifetime unclear
    conn *grpc.ClientConn
}
