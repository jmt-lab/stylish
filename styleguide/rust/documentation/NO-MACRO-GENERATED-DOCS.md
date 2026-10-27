---
type: Styleguide Rule
description: |-
  Write documentation directly with /// and //! instead of generating it
  from macros (e.g. #[doc = concat!(...)] or doc strings passed into
  macro_rules!), so docs are readable in the source.
language: rust
category: documentation
rule_id: NO-MACRO-GENERATED-DOCS
priority: info
tags:
- documentation
- macros
- readability
- google-style
---
Write documentation directly with /// and //! instead of generating it
from macros (e.g. #[doc = concat!(...)] or doc strings passed into
macro_rules!), so docs are readable in the source.

## Good

- /// Maximum number of retries before giving up.
pub const MAX_RETRIES: u32 = 5;

## Bad

- #[doc = concat!("Maximum number of ", "retries", " before giving up.")]
pub const MAX_RETRIES: u32 = 5;
