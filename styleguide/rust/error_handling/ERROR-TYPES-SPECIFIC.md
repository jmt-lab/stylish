---
type: Styleguide Rule
description: |-
  Create specific error types for different failure modes. Avoid
  generic String errors that lose type information.
language: rust
category: error_handling
rule_id: ERROR-TYPES-SPECIFIC
priority: warn
tags:
- errors
- types
- design
---
Create specific error types for different failure modes. Avoid
generic String errors that lose type information.

## Good

- #[derive(Debug)]
enum LoadError {
    IoError(io::Error),
    ParseError(String),
    VersionMismatch { expected: u32, found: u32 }
}

## Bad

- fn load() -> Result<Data, String> // Lost type info
