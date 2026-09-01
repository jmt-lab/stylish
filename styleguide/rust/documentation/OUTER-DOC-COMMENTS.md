---
type: Styleguide Rule
description: |-
  Use outer doc comments (///) instead of inner doc comments (//!),
  except for module/crate-level documentation.
language: rust
category: documentation
rule_id: OUTER-DOC-COMMENTS
priority: warn
tags:
- documentation
- comments
- official
---
Use outer doc comments (///) instead of inner doc comments (//!),
except for module/crate-level documentation.

## Good

- /// Outer doc comment for function
fn process() {}
- //! Module-level documentation at top of file

## Bad

- fn process() {
    //! Wrong: inner doc in function
}
