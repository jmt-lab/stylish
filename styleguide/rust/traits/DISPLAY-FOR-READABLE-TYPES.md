---
type: Styleguide Rule
description: |-
  Implement Display for types meant to be read by people: error types,
  string-like wrappers, identifiers, and values shown in UIs or logs.
language: rust
category: traits
rule_id: DISPLAY-FOR-READABLE-TYPES
priority: info
tags:
- traits
- display
- beautiful-rust
---
Implement Display for types meant to be read by people: error types,
string-like wrappers, identifiers, and values shown in UIs or logs.

## Good

- impl fmt::Display for OrderId {
    fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
        write!(f, "ORD-{:08}", self.0)
    }
}

## Bad

- println!("processing {:?}", order_id); // prints OrderId(42) because there is no Display
