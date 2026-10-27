---
type: Styleguide Rule
description: |-
  Treat items marked #[doc(hidden)] in code you don't own as private. They
  carry no stability guarantees and may change or disappear in any release.
language: rust
category: safety
rule_id: NO-DOC-HIDDEN-ACCESS
priority: error
tags:
- safety
- compatibility
- dependencies
- google-style
---
Treat items marked #[doc(hidden)] in code you don't own as private. They
carry no stability guarantees and may change or disappear in any release.

## Good

- let value = serde_json::from_str::<Config>(input)?;

## Bad

- let value = some_crate::__private::Deserializer::new(input); // #[doc(hidden)] internals
