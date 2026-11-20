---
type: Styleguide Rule
description: |-
  Store collections that never grow after construction as Box<[T]>,
  Box<str>, or Arc<str> rather than Vec<T> or String. You drop the
  capacity word and excess allocation, and the type documents that the
  data is frozen.
language: rust
category: memory
rule_id: BOXED-SLICE-FOR-FROZEN-DATA
priority: info
tags:
- memory
- allocation
- collections
- rust-skills
---
Store collections that never grow after construction as Box<[T]>,
Box<str>, or Arc<str> rather than Vec<T> or String. You drop the
capacity word and excess allocation, and the type documents that the
data is frozen.

## Good

- struct Symbol {
    name: Arc<str>, // shared, immutable, two words
}

let keywords: Box<[&str]> = KEYWORDS.iter().copied().collect();

## Bad

- struct Symbol {
    name: String, // three words plus spare capacity, never mutated
}
