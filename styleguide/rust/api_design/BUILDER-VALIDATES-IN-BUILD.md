---
type: Styleguide Rule
description: |-
  Builder setters are infallible and named after the field; all
  validation, including cross-field checks, happens in a fallible build()
  returning Result. With bon, put #[builder] on a constructor that returns
  Result.
language: rust
category: api_design
rule_id: BUILDER-VALIDATES-IN-BUILD
priority: warn
tags:
- api-design
- builder
- validation
- beautiful-rust
---
Builder setters are infallible and named after the field; all
validation, including cross-field checks, happens in a fallible build()
returning Result. With bon, put #[builder] on a constructor that returns
Result.

## Good

- #[bon::bon]
impl Server {
    #[builder]
    pub fn new(port: u16, workers: usize) -> Result<Self, ConfigError> {
        ensure!(workers > 0, NoWorkersSnafu);
        Ok(Self { port, workers })
    }
}

## Bad

- impl ServerBuilder {
    pub fn set_workers(mut self, workers: usize) -> Result<Self, ConfigError> { ... }
} // fallible, set_-prefixed setter; cross-field checks can't happen here
