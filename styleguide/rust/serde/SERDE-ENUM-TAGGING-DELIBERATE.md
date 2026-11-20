---
type: Styleguide Rule
description: |-
  Choose an enum's representation on purpose: externally tagged (the
  default), internally tagged with #[serde(tag = "type")], adjacently
  tagged, or untagged. The choice is part of the wire contract. Avoid
  untagged for anything but genuinely shape-distinct variants, because its
  errors are vague and it tries variants in order.
language: rust
category: serde
rule_id: SERDE-ENUM-TAGGING-DELIBERATE
priority: warn
tags:
- serde
- enums
- serialization
- api
- rust-skills
---
Choose an enum's representation on purpose: externally tagged (the
default), internally tagged with #[serde(tag = "type")], adjacently
tagged, or untagged. The choice is part of the wire contract. Avoid
untagged for anything but genuinely shape-distinct variants, because its
errors are vague and it tries variants in order.

## Good

- #[derive(Serialize, Deserialize)]
#[serde(tag = "type", rename_all = "snake_case")]
enum Message {
    Ping,
    Publish { topic: String, payload: Bytes },
}

## Bad

- #[derive(Serialize, Deserialize)]
#[serde(untagged)] // "data did not match any variant" on every typo
enum Message {
    Ping {},
    Publish { topic: String, payload: Bytes },
}
