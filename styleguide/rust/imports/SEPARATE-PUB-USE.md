---
type: Styleguide Rule
description: Add newline between regular imports and pub use re-exports to clarify public API
language: rust
category: imports
rule_id: SEPARATE-PUB-USE
priority: warn
tags:
- imports
- api-design
- code-organization
---
Add newline between regular imports and pub use re-exports to clarify public API

## Good

- use std::collections::HashMap;
use serde::Serialize;

pub use crate::types::MyType;


## Bad

- use std::collections::HashMap;
pub use crate::types::MyType;
use serde::Serialize;

