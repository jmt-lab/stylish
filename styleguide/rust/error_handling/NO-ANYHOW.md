---
type: Styleguide Rule
description: |-
  anyhow is prohibited. While convenient, anyhow encourages lazy error
  handling by making it too easy to propagate errors without adding
  context. It erases type information and makes error handling an
  afterthought. Use SNAFU instead, which requires explicit context
  at each error site.
language: rust
category: error_handling
rule_id: NO-ANYHOW
priority: error
tags:
- errors
- anyhow
- prohibited
- libraries
---
anyhow is prohibited. While convenient, anyhow encourages lazy error
handling by making it too easy to propagate errors without adding
context. It erases type information and makes error handling an
afterthought. Use SNAFU instead, which requires explicit context
at each error site.

## Good

- use snafu::{ResultExt, Snafu};

#[derive(Debug, Snafu)]
enum AppError {
    #[snafu(display("Database connection failed"))]
    Database { source: sqlx::Error },
}

fn connect() -> Result<Pool, AppError> {
    Pool::connect(url).context(DatabaseSnafu)
}


## Bad

- use anyhow::{Context, Result};

fn connect() -> Result<Pool> {
    Pool::connect(url).context("database connection failed")
}

- // anyhow in Cargo.toml
[dependencies]
anyhow = "1.0"

