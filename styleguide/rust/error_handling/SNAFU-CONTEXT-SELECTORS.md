---
type: Styleguide Rule
description: |-
  Always use SNAFU's generated context selectors (e.g., FooSnafu) with
  the .context() method. This pattern ensures every error site explicitly
  adds relevant context. Never use .map_err() to convert to SNAFU errors.
language: rust
category: error_handling
rule_id: SNAFU-CONTEXT-SELECTORS
priority: error
tags:
- errors
- snafu
- context
- patterns
---
Always use SNAFU's generated context selectors (e.g., FooSnafu) with
the .context() method. This pattern ensures every error site explicitly
adds relevant context. Never use .map_err() to convert to SNAFU errors.

## Good

- use snafu::ResultExt;

let file = File::open(&path).context(OpenFileSnafu { path: &path })?;
let data = serde_json::from_reader(file).context(ParseJsonSnafu)?;


## Bad

- // Using map_err instead of context selector
let file = File::open(&path)
    .map_err(|e| Error::OpenFile { source: e, path: path.clone() })?;

