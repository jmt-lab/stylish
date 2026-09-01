---
type: Styleguide Rule
description: |-
  thiserror is prohibited. While it reduces boilerplate for error types,
  it doesn't provide the context selector pattern that SNAFU offers.
  SNAFU's selectors make error construction explicit and ensure context
  is added at the point of failure. Use SNAFU for all custom error types.
language: rust
category: error_handling
rule_id: NO-THISERROR
priority: error
tags:
- errors
- thiserror
- prohibited
- libraries
---
thiserror is prohibited. While it reduces boilerplate for error types,
it doesn't provide the context selector pattern that SNAFU offers.
SNAFU's selectors make error construction explicit and ensure context
is added at the point of failure. Use SNAFU for all custom error types.

## Good

- use snafu::Snafu;

#[derive(Debug, Snafu)]
enum ParseError {
    #[snafu(display("Invalid header at line {line}"))]
    InvalidHeader { line: usize },
    
    #[snafu(display("Unexpected token: {token}"))]
    UnexpectedToken { token: String },
}


## Bad

- use thiserror::Error;

#[derive(Debug, Error)]
enum ParseError {
    #[error("Invalid header at line {0}")]
    InvalidHeader(usize),
    
    #[error("Unexpected token: {0}")]
    UnexpectedToken(String),
}

- // thiserror in Cargo.toml
[dependencies]
thiserror = "1.0"

