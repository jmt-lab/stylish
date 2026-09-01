---
type: Styleguide Rule
description: Use single space before and after equals signs in attributes.
language: rust
category: attributes
rule_id: ATTR-EQUALS-SPACING
priority: warn
tags:
- attributes
- spacing
---
Use single space before and after equals signs in attributes.

## Good

- #[foo = 42]

## Bad

- #[foo=42]
