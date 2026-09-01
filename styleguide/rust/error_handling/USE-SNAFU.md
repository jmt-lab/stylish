---
type: Styleguide Rule
description: |-
  SNAFU (Situation Normal: All Fouled Up) is the required error handling
  library. It provides context selectors that make error creation explicit,
  automatic backtrace capture, and clean error chaining. SNAFU forces you
  to think about error context at each call site.
language: rust
category: error_handling
rule_id: USE-SNAFU
priority: error
tags:
- errors
- snafu
- libraries
- mandatory
---
SNAFU (Situation Normal: All Fouled Up) is the required error handling
library. It provides context selectors that make error creation explicit,
automatic backtrace capture, and clean error chaining. SNAFU forces you
to think about error context at each call site.

## Good

- use snafu::{ResultExt, Snafu};

#[derive(Debug, Snafu)]
enum Error {
    #[snafu(display("Failed to read config from {path}"))]
    ReadConfig { source: std::io::Error, path: PathBuf },
    
    #[snafu(display("Failed to parse config"))]
    ParseConfig { source: toml::de::Error },
}

fn load_config(path: &Path) -> Result<Config, Error> {
    let contents = std::fs::read_to_string(path)
        .context(ReadConfigSnafu { path })?;
    let config: Config = toml::from_str(&contents)
        .context(ParseConfigSnafu)?;
    Ok(config)
}


## Bad

- // Using anyhow - too permissive, hides error structure
fn load_config(path: &Path) -> anyhow::Result<Config> {
    let contents = std::fs::read_to_string(path)?;
    let config: Config = toml::from_str(&contents)?;
    Ok(config)
}

