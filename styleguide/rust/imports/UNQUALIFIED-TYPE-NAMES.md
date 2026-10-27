---
type: Styleguide Rule
description: |-
  Import types and traits and refer to them unqualified (Regex, not
  regex::Regex). Exceptions: ambiguous common names like io::Error (or rename
  with `as`), large groups of related types (e.g. hir::), macros and generated
  code, and files where importing everything would bloat the import block.
language: rust
category: imports
rule_id: UNQUALIFIED-TYPE-NAMES
priority: warn
tags:
- imports
- types
- readability
- google-style
---
Import types and traits and refer to them unqualified (Regex, not
regex::Regex). Exceptions: ambiguous common names like io::Error (or rename
with `as`), large groups of related types (e.g. hir::), macros and generated
code, and files where importing everything would bloat the import block.

## Good

- use regex::Regex;

fn matcher() -> Regex { ... }
- fn read() -> Result<Vec<u8>, io::Error> { ... } // ambiguous name kept qualified

## Bad

- fn matcher() -> regex::Regex { ... }
- let map: std::collections::HashMap<String, u32> = std::collections::HashMap::new();
