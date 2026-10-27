---
type: Styleguide Rule
description: |-
  Public error types implement std::error::Error (SNAFU derives it) and are
  Send + Sync + 'static so they can cross threads and be downcast. Never use
  (), String, or Box<dyn Error> as a library's public error type.
language: rust
category: error_handling
rule_id: ERRORS-SEND-SYNC-STATIC
priority: warn
tags:
- error-handling
- errors
- concurrency
- beautiful-rust
---
Public error types implement std::error::Error (SNAFU derives it) and are
Send + Sync + 'static so they can cross threads and be downcast. Never use
(), String, or Box<dyn Error> as a library's public error type.

## Good

- #[derive(Debug, Snafu)]
pub enum FetchError {
    #[snafu(display("Request to {url} failed"))]
    Request { url: String, source: reqwest::Error },
}

const _: () = { const fn check<E: Error + Send + Sync + 'static>() {} check::<FetchError>(); };

## Bad

- pub fn fetch(url: &str) -> Result<Body, Box<dyn Error>> { ... }
- pub fn fetch(url: &str) -> Result<Body, ()> { ... }
