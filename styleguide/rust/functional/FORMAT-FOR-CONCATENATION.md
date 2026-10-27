---
type: Styleguide Rule
description: |-
  Use format!() / write!() to concatenate more than two strings or to
  substitute values into a literal template, instead of chained + or
  str::replace on placeholder text. It allocates less and avoids inventing a
  templating syntax.
language: rust
category: functional
rule_id: FORMAT-FOR-CONCATENATION
priority: info
tags:
- strings
- formatting
- performance
- google-style
---
Use format!() / write!() to concatenate more than two strings or to
substitute values into a literal template, instead of chained + or
str::replace on placeholder text. It allocates less and avoids inventing a
templating syntax.

## Good

- let url = format!("{scheme}://{host}:{port}{path}");
- write!(out, "Hello, {name}!")?;

## Bad

- let url = scheme.to_string() + "://" + &host + ":" + &port.to_string() + &path;
- let greeting = "Hello, {name}!".replace("{name}", &name);
