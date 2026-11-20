---
type: Styleguide Rule
description: |-
  Log an error once, at the place that handles it, and include its full
  source chain. Code that propagates an error with ? doesn't also log it,
  and the handler doesn't log only the outermost message.
language: rust
category: observability
rule_id: LOG-ERRORS-ONCE-WITH-CHAIN
priority: warn
tags:
- observability
- errors
- logging
- rust-skills
---
Log an error once, at the place that handles it, and include its full
source chain. Code that propagates an error with ? doesn't also log it,
and the handler doesn't log only the outermost message.

## Good

- if let Err(error) = sync_inventory().await {
    // snafu::Report renders the whole chain of sources.
    tracing::error!(error = %snafu::Report::from_error(&error), "inventory sync failed");
}

## Bad

- let rows = fetch_rows().await.map_err(|error| {
    tracing::error!("fetch failed: {error}"); // logged here...
    error
})?; // ...and again by every caller up the stack
