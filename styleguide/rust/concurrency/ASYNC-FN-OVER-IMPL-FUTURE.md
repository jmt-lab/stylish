---
type: Styleguide Rule
description: |-
  Write async fn rather than fn -> impl Future, except in traits or hot
  paths where setup must run before the future is created.
language: rust
category: concurrency
rule_id: ASYNC-FN-OVER-IMPL-FUTURE
priority: info
tags:
- concurrency
- async
- beautiful-rust
---
Write async fn rather than fn -> impl Future, except in traits or hot
paths where setup must run before the future is created.

## Good

- pub async fn fetch(&self, id: Id) -> Result<Item, FetchError> { ... }

## Bad

- pub fn fetch(&self, id: Id) -> impl Future<Output = Result<Item, FetchError>> + '_ { async move { ... } }
