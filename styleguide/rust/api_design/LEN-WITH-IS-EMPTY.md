---
type: Styleguide Rule
description: |-
  Implement expected API sets together: if a type has a public len(), also
  provide is_empty() (Clippy: len_without_is_empty).
language: rust
category: api_design
rule_id: LEN-WITH-IS-EMPTY
priority: warn
tags:
- api-design
- collections
- clippy
- google-style
---
Implement expected API sets together: if a type has a public len(), also
provide is_empty() (Clippy: len_without_is_empty).

## Good

- impl Queue {
    pub fn len(&self) -> usize { self.items.len() }
    pub fn is_empty(&self) -> bool { self.items.is_empty() }
}

## Bad

- impl Queue {
    pub fn len(&self) -> usize { self.items.len() }
} // callers must write queue.len() == 0
