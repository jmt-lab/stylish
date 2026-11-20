---
type: Styleguide Rule
description: |-
  Mark fields added to an existing format with #[serde(default)] (or
  default = "path") so documents written before the field existed still
  deserialize. Use a container-level #[serde(default)] for config structs
  whose every field has a sensible Default.
language: rust
category: serde
rule_id: SERDE-DEFAULT-FOR-COMPATIBILITY
priority: warn
tags:
- serde
- compatibility
- configuration
- rust-skills
---
Mark fields added to an existing format with #[serde(default)] (or
default = "path") so documents written before the field existed still
deserialize. Use a container-level #[serde(default)] for config structs
whose every field has a sensible Default.

## Good

- #[derive(Deserialize)]
struct ServerConfig {
    address: SocketAddr,
    #[serde(default = "default_worker_count")]
    workers: usize, // added in v2; v1 files omit it
}

## Bad

- #[derive(Deserialize)]
struct ServerConfig {
    address: SocketAddr,
    workers: usize, // every v1 config file now fails with "missing field"
}
