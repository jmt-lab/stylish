---
type: Styleguide Rule
description: |-
  Give lifetimes descriptive names, especially lifetimes on types. Use '_
  wherever it works. Single-letter lifetimes are fine for simple input/output
  relationships in a function signature or local for<'a> bounds, but use at
  most two; past that, name them.
language: rust
category: naming
rule_id: DESCRIPTIVE-LIFETIMES
priority: info
tags:
- naming
- lifetimes
- readability
- google-style
---
Give lifetimes descriptive names, especially lifetimes on types. Use '_
wherever it works. Single-letter lifetimes are fine for simple input/output
relationships in a function signature or local for<'a> bounds, but use at
most two; past that, name them.

## Good

- pub struct Parser<'source> {
    input: &'source str,
}
- fn first_word(text: &str) -> &str { ... } // elided
- fn longest<'a>(a: &'a str, b: &'a str) -> &'a str { ... }

## Bad

- pub struct Request<'a, 'b, 'c> {
    headers: &'a Headers,
    body: &'b [u8],
    peer: &'c PeerInfo,
}
