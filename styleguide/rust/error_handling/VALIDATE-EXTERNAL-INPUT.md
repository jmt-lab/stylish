---
type: Styleguide Rule
description: |-
  Never trust external data (files, network, user input). Validate
  thoroughly and return Result for invalid input.
language: rust
category: error_handling
rule_id: VALIDATE-EXTERNAL-INPUT
priority: error
tags:
- validation
- security
- safety
- carmack
---
Never trust external data (files, network, user input). Validate
thoroughly and return Result for invalid input.

## Good

- fn parse_size(input: &str) -> Result<usize, ParseError> {
    let size = input.parse()?;
    if size > MAX_SIZE {
        return Err(ParseError::TooLarge);
    }
    Ok(size)
}

## Bad

- fn parse_size(input: &str) -> usize {
    input.parse().unwrap() // Can panic on bad input
}
