---
type: Styleguide Rule
description: |-
  Don't put derivable trait bounds (Clone, Debug, PartialEq, Default,
  Serialize, ...) on struct or enum definitions; put them on the impl blocks
  that need them. Exceptions: associated-type references, ?Sized, or a Drop
  impl that needs the bound.
language: rust
category: traits
rule_id: NO-STRUCT-TRAIT-BOUNDS
priority: warn
tags:
- traits
- generics
- bounds
- beautiful-rust
---
Don't put derivable trait bounds (Clone, Debug, PartialEq, Default,
Serialize, ...) on struct or enum definitions; put them on the impl blocks
that need them. Exceptions: associated-type references, ?Sized, or a Drop
impl that needs the bound.

## Good

- #[derive(Clone, Debug)]
pub struct Cache<K, V> { entries: HashMap<K, V> }

impl<K: Hash + Eq, V: Clone> Cache<K, V> { ... }

## Bad

- pub struct Cache<K: Hash + Eq + Clone + Debug, V: Clone + Debug> { entries: HashMap<K, V> }
