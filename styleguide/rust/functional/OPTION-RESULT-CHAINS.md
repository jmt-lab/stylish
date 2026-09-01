---
type: Styleguide Rule
description: |-
  Use map, and_then, or_else to chain operations on Option/Result.
  This creates clean pipelines without nested matches.
language: rust
category: functional
rule_id: OPTION-RESULT-CHAINS
priority: warn
tags:
- functional
- option
- result
- chaining
---
Use map, and_then, or_else to chain operations on Option/Result.
This creates clean pipelines without nested matches.

## Good

- fn parse_config(input: &str) -> Option<Config> {
    tokenize(input)
        .and_then(|tokens| validate(&tokens))
        .and_then(|valid| build_config(valid))
}

## Bad

- fn parse_config(input: &str) -> Option<Config> {
    match tokenize(input) {
        Some(tokens) => match validate(&tokens) {
            Some(valid) => build_config(valid),
            None => None,
        },
        None => None,
    }
}
