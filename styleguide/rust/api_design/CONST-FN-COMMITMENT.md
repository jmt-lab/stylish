---
type: Styleguide Rule
description: |-
  Mark a public function const only if you expect it to stay const (or
  will help callers migrate). Removing const later is a breaking change
  because callers may use the function in const contexts.
language: rust
category: api_design
rule_id: CONST-FN-COMMITMENT
priority: warn
tags:
- api-design
- const
- semver
- compatibility
- google-style
---
Mark a public function const only if you expect it to stay const (or
will help callers migrate). Removing const later is a breaking change
because callers may use the function in const contexts.

## Good

- pub const fn from_millis(ms: u64) -> Self { Self { nanos: ms * 1_000_000 } } // stable arithmetic

## Bad

- pub const fn default_timeout() -> Duration { Duration::from_secs(30) }
// planned to read from config later; dropping const will break callers
