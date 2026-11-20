---
type: Styleguide Rule
description: |-
  Libraries emit events through the tracing or log facade and never
  install a global subscriber or logger. Only the binary decides where
  logs go, at what level, and in what format.
language: rust
category: observability
rule_id: LIBRARIES-NEVER-INSTALL-SUBSCRIBERS
priority: error
tags:
- observability
- tracing
- libraries
- rust-skills
---
Libraries emit events through the tracing or log facade and never
install a global subscriber or logger. Only the binary decides where
logs go, at what level, and in what format.

## Good

- // library
tracing::debug!(entries = index.len(), "index loaded");

// main.rs
tracing_subscriber::fmt().with_env_filter(EnvFilter::from_default_env()).init();

## Bad

- // library
pub fn open(path: &Path) -> Result<Index, IndexError> {
    tracing_subscriber::fmt().init(); // panics or fights the application's subscriber
    // ...
}
