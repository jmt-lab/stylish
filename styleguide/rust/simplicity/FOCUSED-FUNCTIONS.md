---
type: Styleguide Rule
description: Functions should have one clear purpose and responsibility. Extract mixed concerns into separate functions. Split functions exceeding 50 lines of code excluding blank lines and comments, unless they are simple sequential operations, performance-critical loops, or generated code.
language: rust
category: simplicity
rule_id: FOCUSED-FUNCTIONS
priority: warn
tags:
- simplicity
- code-organization
- maintainability
---
Functions should have one clear purpose and responsibility. Extract mixed concerns into separate functions. Split functions exceeding 50 lines of code excluding blank lines and comments, unless they are simple sequential operations, performance-critical loops, or generated code.

## Good

- Functions with single responsibility
- Use ? operator for error propagation
- Extract match arms into handler functions

## Bad

- Functions handling multiple unrelated concerns
- Large functions with complex nested logic
