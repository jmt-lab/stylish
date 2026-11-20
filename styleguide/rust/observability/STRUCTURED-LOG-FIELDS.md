---
type: Styleguide Rule
description: |-
  Record values as structured key-value fields, not interpolated into the
  message. A constant message with fields can be filtered, aggregated, and
  indexed; a formatted string cannot.
language: rust
category: observability
rule_id: STRUCTURED-LOG-FIELDS
priority: warn
tags:
- observability
- tracing
- logging
- rust-skills
---
Record values as structured key-value fields, not interpolated into the
message. A constant message with fields can be filtered, aggregated, and
indexed; a formatted string cannot.

## Good

- tracing::info!(user_id = %user.id, elapsed_ms = elapsed.as_millis(), "login succeeded");

## Bad

- tracing::info!("login succeeded for user {} after {}ms", user.id, elapsed.as_millis());
