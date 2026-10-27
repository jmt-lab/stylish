---
type: Styleguide Rule
description: |-
  Don't use glob imports. They hide where names come from and make
  large-scale refactors harder. Allowed exceptions: use super::* in inline
  (e.g. test) modules, use Enum::* inside functions that primarily deal with
  that enum, pub use submodule::* re-exports in non-leaf modules, and preludes
  (see PRELUDE-FOR-COMMON-IMPORTS).
language: rust
category: imports
rule_id: NO-GLOB-IMPORTS
priority: warn
tags:
- imports
- readability
- google-style
---
Don't use glob imports. They hide where names come from and make
large-scale refactors harder. Allowed exceptions: use super::* in inline
(e.g. test) modules, use Enum::* inside functions that primarily deal with
that enum, pub use submodule::* re-exports in non-leaf modules, and preludes
(see PRELUDE-FOR-COMMON-IMPORTS).

## Good

- use std::collections::{BTreeMap, HashMap};
- #[cfg(test)]
mod tests {
    use super::*;
}
- fn describe(shape: Shape) -> &'static str {
    use Shape::*;
    match shape {
        Circle => "circle",
        Square => "square",
    }
}

## Bad

- use std::collections::*;
- use crate::config::*; // which items does this module actually need?
