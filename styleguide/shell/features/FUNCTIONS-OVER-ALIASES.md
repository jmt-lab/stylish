---
type: Styleguide Rule
description: Prefer functions over aliases. Functions are more portable, can be exported, and work in scripts.
language: shell
category: features
rule_id: FUNCTIONS-OVER-ALIASES
priority: warn
tags:
- portability
- functions
- best-practice
---
Prefer functions over aliases. Functions are more portable, can be exported, and work in scripts.

## Good

- ll() {
  ls -lah "$@"
}


## Bad

- alias ll='ls -lah'
