---
type: Styleguide Rule
description: |-
  Match the external wire format's naming convention with one
  container-level #[serde(rename_all = "...")] instead of renaming fields
  one by one. Rust identifiers stay snake_case and UpperCamelCase.
language: rust
category: serde
rule_id: SERDE-RENAME-ALL
priority: info
tags:
- serde
- naming
- serialization
- rust-skills
---
Match the external wire format's naming convention with one
container-level #[serde(rename_all = "...")] instead of renaming fields
one by one. Rust identifiers stay snake_case and UpperCamelCase.

## Good

- #[derive(Serialize, Deserialize)]
#[serde(rename_all = "camelCase")]
struct UserProfile {
    display_name: String,
    created_at: Timestamp,
}

## Bad

- #[derive(Serialize, Deserialize)]
struct UserProfile {
    #[serde(rename = "displayName")]
    display_name: String,
    #[allow(non_snake_case)]
    createdAt: Timestamp,
}
