---
type: Styleguide Rule
description: Group multiple items from the same module using nested paths like `use std::io::{Read, Write}`
language: rust
category: imports
rule_id: NESTED-SAME-MODULE
priority: warn
tags:
- imports
- code-organization
- readability
---
Group multiple items from the same module using nested paths like `use std::io::{Read, Write}`

## Good

- use std::io::{Read, Write};

## Bad

- use std::io::Read;
use std::io::Write;

