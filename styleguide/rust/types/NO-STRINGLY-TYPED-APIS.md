---
type: Styleguide Rule
description: |-
  Don't pass closed sets of values, identifiers, or structured data as
  String or &str. Use an enum for a closed set, a newtype for an
  identifier, and a parsed type for structured text, converting at the
  boundary with FromStr or serde.
language: rust
category: types
rule_id: NO-STRINGLY-TYPED-APIS
priority: warn
tags:
- types
- api-design
- enums
- newtypes
- rust-skills
---
Don't pass closed sets of values, identifiers, or structured data as
String or &str. Use an enum for a closed set, a newtype for an
identifier, and a parsed type for structured text, converting at the
boundary with FromStr or serde.

## Good

- pub enum Region { UsEast1, EuWest1 }

pub fn deploy(service: &ServiceName, region: Region) -> Result<(), DeployError> { /* ... */ }

## Bad

- pub fn deploy(service: &str, region: &str) -> Result<(), DeployError> {
    if region != "us-east-1" && region != "eu-west-1" { /* ... */ }
}
