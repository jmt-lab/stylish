---
type: Styleguide Rule
description: |-
  Await independent futures concurrently with join! or try_join! instead
  of one after another. Sequential awaits add their latencies together;
  try_join! also returns as soon as any branch fails.
language: rust
category: concurrency
rule_id: JOIN-INDEPENDENT-FUTURES
priority: warn
tags:
- concurrency
- async
- join
- rust-skills
---
Await independent futures concurrently with join! or try_join! instead
of one after another. Sequential awaits add their latencies together;
try_join! also returns as soon as any branch fails.

## Good

- let (user, orders) = tokio::try_join!(
    fetch_user(&client, user_id),
    fetch_orders(&client, user_id),
)?;

## Bad

- let user = fetch_user(&client, user_id).await?;
let orders = fetch_orders(&client, user_id).await?; // waits for user first
