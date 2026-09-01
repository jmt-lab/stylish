---
type: Styleguide Rule
description: |-
  Enable SNAFU's backtrace feature in Cargo.toml and include backtrace
  fields in error variants. For variants WITH a source error, SNAFU
  captures backtraces automatically via the source chain. For variants
  WITHOUT a source, you MUST add a backtrace field explicitly.
language: rust
category: error_handling
rule_id: SNAFU-BACKTRACE
priority: error
tags:
- errors
- snafu
- backtrace
- debugging
- mandatory
---
Enable SNAFU's backtrace feature in Cargo.toml and include backtrace
fields in error variants. For variants WITH a source error, SNAFU
captures backtraces automatically via the source chain. For variants
WITHOUT a source, you MUST add a backtrace field explicitly.

## Good

- # Cargo.toml
[dependencies]
snafu = { version = "0.8", features = ["backtrace"] }

- #[derive(Debug, Snafu)]
enum Error {
    // Source variant - backtrace captured via source chain
    #[snafu(display("IO operation failed"))]
    Io { source: std::io::Error },
    
    // No source - MUST have explicit backtrace field
    #[snafu(display("Invalid value: {value}"))]
    InvalidValue { value: String, backtrace: snafu::Backtrace },
}


## Bad

- # Missing backtrace feature
snafu = "0.8"

- // No-source variant missing backtrace
#[snafu(display("Not found: {id}"))]
NotFound { id: String },  // No backtrace - will lose stack info!

