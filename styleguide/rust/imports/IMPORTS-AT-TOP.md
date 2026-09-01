---
type: Styleguide Rule
description: 'Place all imports at the top of the file without separating newlines between them. Exception: a blank line before pub use re-exports is required (see SEPARATE-PUB-USE).'
language: rust
category: imports
rule_id: IMPORTS-AT-TOP
priority: error
tags:
- imports
- code-organization
- readability
---
Place all imports at the top of the file without separating newlines between them. Exception: a blank line before pub use re-exports is required (see SEPARATE-PUB-USE).

## Good

- use std::collections::HashMap;
use std::fs::File;
use serde::Serialize;

fn main() {}


## Bad

- use std::collections::HashMap;

use std::fs::File;

fn main() {}

