---
type: Styleguide Rule
description: |-
  Use the most specific std type for the data: PathBuf / &Path for file
  paths, Duration for time spans, SocketAddr / IpAddr for addresses. Keep
  plain integers at public API boundaries rather than NonZero or Saturating
  wrappers, which are fine internally.
language: rust
category: types
rule_id: STRONGEST-STD-TYPE
priority: warn
tags:
- types
- std
- type-safety
- beautiful-rust
---
Use the most specific std type for the data: PathBuf / &Path for file
paths, Duration for time spans, SocketAddr / IpAddr for addresses. Keep
plain integers at public API boundaries rather than NonZero or Saturating
wrappers, which are fine internally.

## Good

- pub fn retry(path: &Path, delay: Duration) -> Result<(), RetryError> { ... }

## Bad

- pub fn retry(path: &str, delay_ms: u64) -> Result<(), RetryError> { ... }
