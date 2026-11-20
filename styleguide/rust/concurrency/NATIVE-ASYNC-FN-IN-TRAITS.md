---
type: Styleguide Rule
description: |-
  Write async fn directly in traits (stable since Rust 1.75) instead of
  using the async_trait macro, which boxes every returned future. Keep
  async_trait or a manual Box<dyn Future> only when the trait must be used
  as dyn Trait. For public traits, use the return-type form to promise a
  Send future.
language: rust
category: concurrency
rule_id: NATIVE-ASYNC-FN-IN-TRAITS
priority: warn
tags:
- concurrency
- async
- traits
- rust-skills
---
Write async fn directly in traits (stable since Rust 1.75) instead of
using the async_trait macro, which boxes every returned future. Keep
async_trait or a manual Box<dyn Future> only when the trait must be used
as dyn Trait. For public traits, use the return-type form to promise a
Send future.

## Good

- pub trait Store {
    fn get(&self, key: &str) -> impl Future<Output = Option<Bytes>> + Send;
}

trait LocalCache {
    async fn refresh(&mut self) -> Result<(), CacheError>;
}

## Bad

- #[async_trait::async_trait]
trait LocalCache {
    async fn refresh(&mut self) -> Result<(), CacheError>; // boxes every call
}
