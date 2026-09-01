---
type: Styleguide Rule
description: Use spaces, not tabs. All indentation must be a multiple of 4 spaces.
language: rust
category: formatting
rule_id: INDENT-SPACES
priority: error
tags:
- formatting
- whitespace
---
Use spaces, not tabs. All indentation must be a multiple of 4 spaces.

## Good

- fn main() {
    let x = 5;
}

## Bad

- fn main() {
	let x = 5;
}
