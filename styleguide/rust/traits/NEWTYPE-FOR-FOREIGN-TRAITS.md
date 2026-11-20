---
type: Styleguide Rule
description: |-
  To implement a foreign trait for a foreign type, which the orphan rule
  forbids, wrap the type in a local newtype. Don't fork the dependency or
  add a parallel trait.
language: rust
category: traits
rule_id: NEWTYPE-FOR-FOREIGN-TRAITS
priority: info
tags:
- traits
- coherence
- orphan-rule
- newtypes
- rust-skills
---
To implement a foreign trait for a foreign type, which the orphan rule
forbids, wrap the type in a local newtype. Don't fork the dependency or
add a parallel trait.

## Good

- struct DisplayPath<'path>(&'path Path);

impl fmt::Display for DisplayPath<'_> {
    fn fmt(&self, formatter: &mut fmt::Formatter<'_>) -> fmt::Result {
        write!(formatter, "{}", self.0.display())
    }
}

## Bad

- impl fmt::Display for Path { /* ... */ } // error[E0117]: only traits defined in the current crate ...
