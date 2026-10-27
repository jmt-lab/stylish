---
type: Styleguide Rule
description: |-
  Do not pass pointers just to save bytes. If a function only reads *x, pass
  x; this covers *string and pointers to interfaces like *io.Reader. Large or
  growing structs and protocol buffer messages should still be passed by
  pointer.
language: go
category: types
rule_id: PASS-VALUES-NOT-POINTERS
priority: warn
tags:
- pointers
- parameters
- google-style
---
Do not pass pointers just to save bytes. If a function only reads *x, pass
x; this covers *string and pointers to interfaces like *io.Reader. Large or
growing structs and protocol buffer messages should still be passed by
pointer.

## Good

- func greet(name string) string
- func copyAll(r io.Reader) error
- func handle(req *pb.Request) error // proto messages by pointer

## Bad

- func greet(name *string) string { return "hi " + *name }
- func copyAll(r *io.Reader) error
