---
type: Styleguide Rule
description: Attributes with argument lists should be formatted like function calls.
language: rust
category: attributes
rule_id: ATTR-FORMAT-LIKE-FN
priority: warn
tags:
- attributes
- formatting
---
Attributes with argument lists should be formatted like function calls.

## Good

- #[foo(foo, bar)]
- #[long_attribute(
    split,
    across,
)]
