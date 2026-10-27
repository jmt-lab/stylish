---
type: Styleguide Rule
description: |-
  Name extension traits (traits whose sole purpose is to add methods to a
  type from another crate, not to be used in generics or dyn) with an Ext
  suffix. Generally the team owning the extended type should own the
  extension trait, to avoid method name conflicts.
language: rust
category: naming
rule_id: EXTENSION-TRAIT-EXT-SUFFIX
priority: warn
tags:
- naming
- traits
- extension-traits
- google-style
---
Name extension traits (traits whose sole purpose is to add methods to a
type from another crate, not to be used in generics or dyn) with an Ext
suffix. Generally the team owning the extended type should own the
extension trait, to avoid method name conflicts.

## Good

- pub trait PathExt {
    fn is_hidden(&self) -> bool;
}

impl PathExt for Path { ... }

## Bad

- pub trait PathHelpers {
    fn is_hidden(&self) -> bool;
}

impl PathHelpers for Path { ... }
