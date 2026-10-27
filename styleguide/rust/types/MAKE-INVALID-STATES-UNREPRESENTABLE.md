---
type: Styleguide Rule
description: |-
  Encode invariants in types instead of comments: use data-carrying enums
  rather than "field X is only meaningful when Y is set", and validate once
  in a fallible constructor. Then the compiler enforces what a comment only
  requests.
language: rust
category: types
rule_id: MAKE-INVALID-STATES-UNREPRESENTABLE
priority: warn
tags:
- types
- enums
- invariants
- type-safety
- beautiful-rust
---
Encode invariants in types instead of comments: use data-carrying enums
rather than "field X is only meaningful when Y is set", and validate once
in a fallible constructor. Then the compiler enforces what a comment only
requests.

## Good

- pub enum Connection {
    Disconnected,
    Connecting { attempt: u32 },
    Connected { session: Session },
}

## Bad

- pub struct Connection {
    pub connected: bool,
    pub session: Option<Session>, // must be Some iff connected
    pub attempt: u32,             // only meaningful while connecting
}
