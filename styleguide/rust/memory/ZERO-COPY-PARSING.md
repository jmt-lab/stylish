---
type: Styleguide Rule
description: |-
  When parsing structured data, consider zero-copy approaches that
  borrow from the input rather than allocating.
language: rust
category: memory
rule_id: ZERO-COPY-PARSING
priority: info
tags:
- memory
- parsing
- performance
---
When parsing structured data, consider zero-copy approaches that
borrow from the input rather than allocating.

## Good

- // Borrows from input, no allocation
struct Token<'a> { text: &'a str }

## Bad

- // Allocates copy of every token
struct Token { text: String }
