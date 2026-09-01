---
type: Styleguide Rule
description: |-
  Use mockall or similar for mocking. Mock databases, HTTP clients,
  and file system. Use traits for dependency injection.
language: rust
category: testing
rule_id: MOCK-DEPENDENCIES
priority: warn
tags:
- testing
- mocking
- isolation
---
Use mockall or similar for mocking. Mock databases, HTTP clients,
and file system. Use traits for dependency injection.

## Good

- #[automock]
trait Database {
    fn query(&self, sql: &str) -> Result<Data>;
}


## Bad

- // Tests hit real database
