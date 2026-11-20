---
type: Styleguide Rule
description: |-
  Leave out lifetimes wherever the elision rules already give the right
  answer, and use '_ for an elided lifetime in a type path. Write explicit
  lifetimes only when the signature ties outputs to particular inputs, and
  then name them descriptively (DESCRIPTIVE-LIFETIMES).
language: rust
category: ownership
rule_id: RELY-ON-LIFETIME-ELISION
priority: info
tags:
- ownership
- lifetimes
- clarity
- rust-skills
---
Leave out lifetimes wherever the elision rules already give the right
answer, and use '_ for an elided lifetime in a type path. Write explicit
lifetimes only when the signature ties outputs to particular inputs, and
then name them descriptively (DESCRIPTIVE-LIFETIMES).

## Good

- fn first_line(text: &str) -> &str { /* ... */ }

impl fmt::Display for Report<'_> { /* ... */ }

## Bad

- fn first_line<'a>(text: &'a str) -> &'a str { /* ... */ }

impl<'a> fmt::Display for Report<'a> { /* ... */ }
