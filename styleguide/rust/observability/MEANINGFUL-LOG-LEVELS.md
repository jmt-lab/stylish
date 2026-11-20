---
type: Styleguide Rule
description: |-
  Use log levels consistently: error for failures that need a human, warn
  for degraded but handled conditions, info for rare lifecycle events,
  debug for diagnostics, and trace for per-item detail. Let the binary
  filter with EnvFilter and RUST_LOG instead of hard-coding verbosity.
language: rust
category: observability
rule_id: MEANINGFUL-LOG-LEVELS
priority: info
tags:
- observability
- tracing
- logging
- rust-skills
---
Use log levels consistently: error for failures that need a human, warn
for degraded but handled conditions, info for rare lifecycle events,
debug for diagnostics, and trace for per-item detail. Let the binary
filter with EnvFilter and RUST_LOG instead of hard-coding verbosity.

## Good

- tracing::warn!(attempt, "upstream timed out, retrying");
tracing::trace!(?row, "decoded row");

## Bad

- tracing::error!("decoded row {:?}", row); // per-row noise at error level
tracing::info!(attempt, "upstream timed out, retrying");
