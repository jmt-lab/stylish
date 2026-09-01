---
type: Styleguide Rule
description: |-
  SNAFU display messages should describe what failed, not implementation
  details. Include relevant context variables in the message. Messages
  are user-facing and should be understandable without source code.
language: rust
category: error_handling
rule_id: SNAFU-DISPLAY-MESSAGES
priority: warn
tags:
- errors
- snafu
- readability
---
SNAFU display messages should describe what failed, not implementation
details. Include relevant context variables in the message. Messages
are user-facing and should be understandable without source code.

## Good

- #[derive(Debug, Snafu)]
enum Error {
    #[snafu(display("Failed to connect to database at {url}"))]
    Connect { source: sqlx::Error, url: String },
    
    #[snafu(display("User {user_id} not found"))]
    UserNotFound { user_id: u64 },
}


## Bad

- #[derive(Debug, Snafu)]
enum Error {
    #[snafu(display("Error code 42"))]
    Something { source: std::io::Error },
}

