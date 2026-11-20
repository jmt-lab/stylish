---
type: Styleguide Rule
description: |-
  Customize a single field's encoding with #[serde(with = "module")] (or
  serialize_with and deserialize_with) instead of a hand-written Serialize
  impl for the whole type, or a stringly typed field converted after
  parsing.
language: rust
category: serde
rule_id: SERDE-WITH-FOR-FOREIGN-FORMATS
priority: info
tags:
- serde
- serialization
- rust-skills
---
Customize a single field's encoding with #[serde(with = "module")] (or
serialize_with and deserialize_with) instead of a hand-written Serialize
impl for the whole type, or a stringly typed field converted after
parsing.

## Good

- #[derive(Serialize, Deserialize)]
struct Lease {
    #[serde(with = "humantime_serde")]
    duration: Duration,
}

## Bad

- #[derive(Serialize, Deserialize)]
struct Lease {
    duration: String, // parsed by hand everywhere it is read
}
