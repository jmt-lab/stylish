---
type: Styleguide Rule
description: |-
  .expect() and .unwrap() are appropriate ONLY for invariant violations
  (programmer errors where failure indicates a bug). They are NOT
  appropriate for operations that could legitimately fail at runtime.

  ACCEPTABLE uses of .expect():
  - Invariant violations: conditions that MUST hold if code is correct
  - Test code: where panics are the expected failure mode
  - Static initialization: truly infallible setup done once at startup
  - After validation: when you've already validated the condition

  UNACCEPTABLE uses:
  - I/O operations (files, network, etc.)
  - Parsing user input or external data
  - Any operation that could fail for non-bug reasons

  For fallible operations, create proper SNAFU error variants and use
  .context() instead. In library code, ALWAYS return Result to let
  callers decide how to handle errors.

  When using .expect(), the message should explain the invariant:
  "X must hold because Y" not just "X should work".
language: rust
category: error_handling
rule_id: EXPECT-WITH-CONTEXT
priority: error
tags:
- errors
- expect
- unwrap
- invariants
- mandatory
---
.expect() and .unwrap() are appropriate ONLY for invariant violations
(programmer errors where failure indicates a bug). They are NOT
appropriate for operations that could legitimately fail at runtime.

ACCEPTABLE uses of .expect():
- Invariant violations: conditions that MUST hold if code is correct
- Test code: where panics are the expected failure mode
- Static initialization: truly infallible setup done once at startup
- After validation: when you've already validated the condition

UNACCEPTABLE uses:
- I/O operations (files, network, etc.)
- Parsing user input or external data
- Any operation that could fail for non-bug reasons

For fallible operations, create proper SNAFU error variants and use
.context() instead. In library code, ALWAYS return Result to let
callers decide how to handle errors.

When using .expect(), the message should explain the invariant:
"X must hold because Y" not just "X should work".

## Good

- // Invariant: index validated before use
let idx = validated_index(input)?;
let item = items.get(idx).expect("index validated above");

- // Invariant: static init happens once in main
let config = CONFIG.get().expect("Config initialized in main before use");

- // Invariant: regex is compile-time constant
let re = Regex::new(r"^\d+$").expect("valid regex literal");

- // Test code - panics are expected
#[test]
fn test_parse() {
    let result = parse("valid").expect("test input should parse");
}

- // Library code - return Result, let caller decide
pub fn parse(input: &str) -> Result<Ast, ParseError> {
    // ... proper error handling
}

- // Fallible operation - use proper error handling
let data = std::fs::read_to_string(path)
    .context(ReadFileSnafu { path })?;


## Bad

- // I/O can fail for legitimate reasons
let data = std::fs::read_to_string(path).expect("file exists");

- // User input can be invalid
let num: i32 = input.parse().expect("valid number");

- // Library panicking on bad input
pub fn parse(input: &str) -> Ast {
    input.parse().unwrap() // Panics on bad input!
}

- // Vague message doesn't explain invariant
let x = foo().expect("should work");

