---
type: Styleguide Rule
description: |-
  If a method matches the purpose of a standard library trait (FromStr,
  Default, From, Display, Iterator, Add, ...), implement the trait instead of
  (or in addition to) a custom inherent method (Clippy:
  should_implement_trait).
language: rust
category: traits
rule_id: IMPLEMENT-STD-TRAITS
priority: warn
tags:
- traits
- std
- clippy
- interop
- google-style
---
If a method matches the purpose of a standard library trait (FromStr,
Default, From, Display, Iterator, Add, ...), implement the trait instead of
(or in addition to) a custom inherent method (Clippy:
should_implement_trait).

## Good

- impl FromStr for Version {
    type Err = ParseVersionError;
    fn from_str(s: &str) -> Result<Self, Self::Err> { ... }
}

let version: Version = "1.2.3".parse()?;

## Bad

- impl Version {
    pub fn from_str(s: &str) -> Result<Self, ParseVersionError> { ... }
} // .parse() and generic FromStr code can't use it
