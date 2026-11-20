---
type: Styleguide Rule
description: |-
  Put #[serde(deny_unknown_fields)] on structs you own the input for, such
  as config files and CLI manifests, so typos fail loudly instead of being
  ignored. Leave it off for messages from other services that may add
  fields, and note that it does not combine with #[serde(flatten)].
language: rust
category: serde
rule_id: SERDE-DENY-UNKNOWN-FIELDS
priority: info
tags:
- serde
- configuration
- validation
- rust-skills
---
Put #[serde(deny_unknown_fields)] on structs you own the input for, such
as config files and CLI manifests, so typos fail loudly instead of being
ignored. Leave it off for messages from other services that may add
fields, and note that it does not combine with #[serde(flatten)].

## Good

- #[derive(Deserialize)]
#[serde(deny_unknown_fields)]
struct BuildConfig {
    target: String,
    #[serde(default)]
    release: bool,
}

## Bad

- #[derive(Deserialize)]
struct BuildConfig {
    target: String,
    #[serde(default)]
    release: bool, // `relase = true` in the file is silently ignored
}
