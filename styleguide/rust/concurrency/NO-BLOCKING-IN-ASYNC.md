---
type: Styleguide Rule
description: |-
  Never call blocking APIs inside async code: std::fs, std::thread::sleep,
  blocking sockets, or synchronous HTTP clients stall the executor thread
  and every task scheduled on it. Use the runtime's async equivalents
  (tokio::fs, tokio::time::sleep) or move the call to spawn_blocking.
language: rust
category: concurrency
rule_id: NO-BLOCKING-IN-ASYNC
priority: error
tags:
- concurrency
- async
- tokio
- blocking
- rust-skills
---
Never call blocking APIs inside async code: std::fs, std::thread::sleep,
blocking sockets, or synchronous HTTP clients stall the executor thread
and every task scheduled on it. Use the runtime's async equivalents
(tokio::fs, tokio::time::sleep) or move the call to spawn_blocking.

## Good

- async fn load_config(path: &Path) -> Result<String, ConfigError> {
    tokio::fs::read_to_string(path)
        .await
        .context(ReadConfigSnafu { path })
}

- let digest = tokio::task::spawn_blocking(move || hash_file_sync(&path))
    .await
    .expect("hashing task panicked")?;

## Bad

- async fn load_config(path: &Path) -> Result<String, ConfigError> {
    std::fs::read_to_string(path).context(ReadConfigSnafu { path }) // blocks the executor
}

- async fn retry_later() {
    std::thread::sleep(Duration::from_secs(1)); // parks a runtime worker thread
}
