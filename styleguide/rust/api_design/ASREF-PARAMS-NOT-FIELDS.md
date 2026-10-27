---
type: Styleguide Rule
description: |-
  Parameters that only read a path, string, or byte buffer may take
  impl AsRef<Path> / AsRef<str> / AsRef<[u8]> for flexibility. Never use
  AsRef generics for struct fields; store owned PathBuf, String, or Vec<u8>.
language: rust
category: api_design
rule_id: ASREF-PARAMS-NOT-FIELDS
priority: info
tags:
- api-design
- generics
- parameters
- beautiful-rust
---
Parameters that only read a path, string, or byte buffer may take
impl AsRef<Path> / AsRef<str> / AsRef<[u8]> for flexibility. Never use
AsRef generics for struct fields; store owned PathBuf, String, or Vec<u8>.

## Good

- pub fn load(path: impl AsRef<Path>) -> Result<Config, LoadError> { ... }
- pub struct Config { source: PathBuf }

## Bad

- pub struct Config<P: AsRef<Path>> { source: P } // generic leaks into every user
