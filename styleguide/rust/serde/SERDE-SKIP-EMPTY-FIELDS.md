---
type: Styleguide Rule
description: |-
  Omit absent or empty optional fields from output with
  skip_serializing_if (Option::is_none, Vec::is_empty) and pair it with
  default so the field round-trips. This keeps payloads small and avoids
  sending null where the consumer expects absence.
language: rust
category: serde
rule_id: SERDE-SKIP-EMPTY-FIELDS
priority: info
tags:
- serde
- serialization
- rust-skills
---
Omit absent or empty optional fields from output with
skip_serializing_if (Option::is_none, Vec::is_empty) and pair it with
default so the field round-trips. This keeps payloads small and avoids
sending null where the consumer expects absence.

## Good

- #[derive(Serialize, Deserialize)]
struct Event {
    name: String,
    #[serde(default, skip_serializing_if = "Option::is_none")]
    correlation_id: Option<String>,
    #[serde(default, skip_serializing_if = "Vec::is_empty")]
    tags: Vec<String>,
}

## Bad

- #[derive(Serialize, Deserialize)]
struct Event {
    name: String,
    correlation_id: Option<String>, // emits "correlation_id": null
    tags: Vec<String>,              // emits "tags": []
}
