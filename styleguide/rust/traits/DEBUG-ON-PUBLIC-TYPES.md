---
type: Styleguide Rule
description: |-
  Every public type implements Debug (lint: missing_debug_implementations).
  Even empty values should produce non-empty Debug output.
language: rust
category: traits
rule_id: DEBUG-ON-PUBLIC-TYPES
priority: warn
tags:
- traits
- debug
- debuggability
- beautiful-rust
---
Every public type implements Debug (lint: missing_debug_implementations).
Even empty values should produce non-empty Debug output.

## Good

- #[derive(Debug)]
pub struct Client { endpoint: Url, retries: u32 }

## Bad

- pub struct Client { endpoint: Url, retries: u32 } // can't be printed in logs or assertions
