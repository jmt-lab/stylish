---
type: Styleguide Rule
description: |-
  Fix lints rather than silencing them. When a lint is genuinely wrong for
  one item, use #[expect(lint, reason = "...")] on the narrowest item; expect
  warns when the lint stops firing, so stale suppressions get removed. Reserve
  #[allow] for generated code and macro output (Clippy: allow_attributes,
  allow_attributes_without_reason).
language: rust
category: practices
rule_id: EXPECT-LINT-WITH-REASON
priority: warn
tags:
- practices
- lints
- clippy
- beautiful-rust
---
Fix lints rather than silencing them. When a lint is genuinely wrong for
one item, use #[expect(lint, reason = "...")] on the narrowest item; expect
warns when the lint stops firing, so stale suppressions get removed. Reserve
#[allow] for generated code and macro output (Clippy: allow_attributes,
allow_attributes_without_reason).

## Good

- #[expect(clippy::cast_possible_truncation, reason = "value is masked to 16 bits above")]
let port = (raw & 0xffff) as u16;

## Bad

- #![allow(clippy::all)]
- #[allow(clippy::too_many_lines)] // no reason, never revisited
