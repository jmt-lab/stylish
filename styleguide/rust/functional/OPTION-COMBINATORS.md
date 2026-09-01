---
type: Styleguide Rule
description: |-
  map, and_then, unwrap_or reduce nesting compared to explicit
  match statements for simple transformations.
language: rust
category: functional
rule_id: OPTION-COMBINATORS
priority: info
tags:
- functional
- option
- combinators
---
map, and_then, unwrap_or reduce nesting compared to explicit
match statements for simple transformations.

## Good

- let name = config.name.unwrap_or("default");
- let doubled = option.map(|x| x * 2);

## Bad

- let name = match config.name {
    Some(n) => n,
    None => "default",
};
