---
type: Styleguide Rule
description: |-
  When accepting borrowed immutable data, borrow the data itself rather
  than the wrapper holding it: &T over &Box<T>, &[T] over &Vec<T>, &str over
  &String, and Option<&T> over &Option<T>. Callers can then pass data held in
  any form without copying it first (Clippy: borrowed_box, ptr_arg).
language: rust
category: api_design
rule_id: BORROW-INNER-DATA-PARAMS
priority: warn
tags:
- api-design
- borrowing
- parameters
- clippy
- google-style
---
When accepting borrowed immutable data, borrow the data itself rather
than the wrapper holding it: &T over &Box<T>, &[T] over &Vec<T>, &str over
&String, and Option<&T> over &Option<T>. Callers can then pass data held in
any form without copying it first (Clippy: borrowed_box, ptr_arg).

## Good

- fn render(node: &Node) { ... }
- fn greet(nickname: Option<&str>) { ... }

## Bad

- fn render(node: &Box<Node>) { ... }
- fn greet(nickname: &Option<String>) { ... }
