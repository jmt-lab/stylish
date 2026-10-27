---
type: Styleguide Rule
description: |-
  Production and library code emits structured events through tracing or
  log, not println!, eprintln!, or dbg!. Pass values as fields rather than
  pre-formatting with format!. Only a CLI's own user-facing output goes to
  stdout (Clippy: print_stdout, print_stderr, dbg_macro).
language: rust
category: practices
rule_id: LOG-NOT-PRINT
priority: warn
tags:
- practices
- logging
- observability
- beautiful-rust
---
Production and library code emits structured events through tracing or
log, not println!, eprintln!, or dbg!. Pass values as fields rather than
pre-formatting with format!. Only a CLI's own user-facing output goes to
stdout (Clippy: print_stdout, print_stderr, dbg_macro).

## Good

- tracing::info!(user_id = %user.id, elapsed_ms = elapsed.as_millis(), "request.completed");

## Bad

- println!("request for user {} finished in {:?}", user.id, elapsed);
- dbg!(&response);
