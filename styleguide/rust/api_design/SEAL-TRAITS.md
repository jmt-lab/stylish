---
type: Styleguide Rule
description: |-
  Seal public traits that downstream crates shouldn't implement, so you can
  add methods later without a breaking change. Document that the trait is
  sealed.
language: rust
category: api_design
rule_id: SEAL-TRAITS
priority: info
tags:
- api-design
- traits
- semver
- future-proofing
- beautiful-rust
---
Seal public traits that downstream crates shouldn't implement, so you can
add methods later without a breaking change. Document that the trait is
sealed.

## Good

- /// A storage backend. This trait is sealed and cannot be implemented
/// outside this crate.
pub trait Backend: private::Sealed { fn name(&self) -> &str; }

mod private {
    pub trait Sealed {}
    impl Sealed for super::Disk {}
}

## Bad

- pub trait Backend { fn name(&self) -> &str; } // adding a required method breaks every external impl
