---
type: Styleguide Rule
description: |-
  Never log credentials, tokens, keys, or personal data. Skip them in
  #[instrument], wrap them in a redacting type (see
  REDACT-SECRETS-IN-DEBUG), and don't log whole request or config structs
  that may contain them.
language: rust
category: observability
rule_id: NEVER-LOG-SECRETS
priority: error
tags:
- observability
- security
- privacy
- logging
- rust-skills
---
Never log credentials, tokens, keys, or personal data. Skip them in
#[instrument], wrap them in a redacting type (see
REDACT-SECRETS-IN-DEBUG), and don't log whole request or config structs
that may contain them.

## Good

- #[tracing::instrument(skip(credentials))]
async fn authenticate(username: &str, credentials: Credentials) -> Result<Session, AuthError> {
    // ...
}

## Bad

- #[tracing::instrument]
async fn authenticate(username: &str, credentials: Credentials) -> Result<Session, AuthError> {
    tracing::debug!(?credentials, "authenticating"); // password in the log store
    // ...
}
