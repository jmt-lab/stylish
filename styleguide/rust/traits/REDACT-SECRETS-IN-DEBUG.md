---
type: Styleguide Rule
description: |-
  Types holding secrets (passwords, tokens, keys) get a hand-written Debug
  (and Display, if any) that redacts the value, plus a unit test asserting the
  secret never appears in the output.
language: rust
category: traits
rule_id: REDACT-SECRETS-IN-DEBUG
priority: error
tags:
- traits
- debug
- display
- security
- secrets
- beautiful-rust
---
Types holding secrets (passwords, tokens, keys) get a hand-written Debug
(and Display, if any) that redacts the value, plus a unit test asserting the
secret never appears in the output.

## Good

- pub struct ApiToken(String);

impl fmt::Debug for ApiToken {
    fn fmt(&self, f: &mut fmt::Formatter<'_>) -> fmt::Result {
        f.write_str("ApiToken(****)")
    }
}

#[test]
fn test_api_token_debug_redacts_secret() {
    assert!(!format!("{:?}", ApiToken("s3cret".into())).contains("s3cret"));
}

## Bad

- #[derive(Debug)]
pub struct ApiToken(String); // prints the token in every log line
