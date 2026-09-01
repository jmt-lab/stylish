---
type: Styleguide Rule
description: Rename conflicting types with `as` keyword or use fully qualified paths for clarity
language: rust
category: imports
rule_id: DISAMBIGUATE-IMPORTS
priority: warn
tags:
- imports
- readability
- modules
---
Rename conflicting types with `as` keyword or use fully qualified paths for clarity

## Good

- use tokio::sync::Mutex as AsyncMutex;
- use std::sync::Mutex;

## Bad

- use tokio::sync::Mutex;
use std::sync::Mutex;

