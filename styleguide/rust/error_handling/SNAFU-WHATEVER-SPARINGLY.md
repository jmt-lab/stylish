---
type: Styleguide Rule
description: |-
  SNAFU's Whatever type is for prototyping only. It behaves like anyhow
  and should be replaced with proper error types before code review.
  Never use Whatever in production code or public APIs.
language: rust
category: error_handling
rule_id: SNAFU-WHATEVER-SPARINGLY
priority: error
tags:
- errors
- snafu
- whatever
- prototyping
---
SNAFU's Whatever type is for prototyping only. It behaves like anyhow
and should be replaced with proper error types before code review.
Never use Whatever in production code or public APIs.

## Good

- // Proper error type for production
#[derive(Debug, Snafu)]
enum ConfigError {
    #[snafu(display("Failed to read {path}"))]
    Read { source: std::io::Error, path: PathBuf },
}


## Bad

- // Whatever is too permissive for production
use snafu::Whatever;

fn load() -> Result<Config, Whatever> {
    let data = std::fs::read_to_string(path)?;
    Ok(toml::from_str(&data)?)
}

