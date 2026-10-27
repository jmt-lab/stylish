---
type: Styleguide Rule
description: |-
  Name iterator types after the method that produces them: iter() returns
  Iter, iter_mut() IterMut, into_iter() IntoIter, keys() Keys, drain() Drain.
language: rust
category: naming
rule_id: ITERATOR-TYPE-NAMES
priority: info
tags:
- naming
- iterators
- official
- beautiful-rust
---
Name iterator types after the method that produces them: iter() returns
Iter, iter_mut() IterMut, into_iter() IntoIter, keys() Keys, drain() Drain.

## Good

- impl Graph {
    pub fn nodes(&self) -> Nodes<'_> { ... }
}
pub struct Nodes<'a> { ... }

## Bad

- impl Graph {
    pub fn nodes(&self) -> GraphNodeIterator<'_> { ... }
}
