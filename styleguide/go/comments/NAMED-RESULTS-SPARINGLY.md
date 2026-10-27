---
type: Styleguide Rule
description: |-
  Name result parameters only when it clarifies godoc: several results of the
  same type, or a result the caller must act on. Do not name results that
  repeat their type, or just to skip declaring a local or to enable naked
  returns.
language: go
category: comments
rule_id: NAMED-RESULTS-SPARINGLY
priority: warn
tags:
- functions
- results
- godoc
- google-style
---
Name result parameters only when it clarifies godoc: several results of the
same type, or a result the caller must act on. Do not name results that
repeat their type, or just to skip declaring a local or to enable naked
returns.

## Good

- func (n *Node) Parent() (*Node, error)
- func (n *Node) Children() (left, right *Node, err error)
- func WithTimeout(parent Context, d time.Duration) (ctx Context, cancel func())

## Bad

- func (n *Node) Parent() (node *Node, err error) // repetitive
- func load() (cfg *Config, err error) { cfg = &Config{}; return } // named only for naked return
