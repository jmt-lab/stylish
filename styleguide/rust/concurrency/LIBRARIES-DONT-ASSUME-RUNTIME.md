---
type: Styleguide Rule
description: |-
  Library code doesn't spawn raw threads or assume a particular async
  runtime. Take an executor or spawn function, or work on impl Read /
  impl AsyncRead supplied by the caller.
language: rust
category: concurrency
rule_id: LIBRARIES-DONT-ASSUME-RUNTIME
priority: warn
tags:
- concurrency
- async
- libraries
- beautiful-rust
---
Library code doesn't spawn raw threads or assume a particular async
runtime. Take an executor or spawn function, or work on impl Read /
impl AsyncRead supplied by the caller.

## Good

- pub async fn sync(&self, io: impl AsyncRead + AsyncWrite + Unpin) -> Result<(), SyncError> { ... }

## Bad

- pub fn start(&self) { tokio::spawn(self.clone().run()); } // panics outside a tokio runtime
