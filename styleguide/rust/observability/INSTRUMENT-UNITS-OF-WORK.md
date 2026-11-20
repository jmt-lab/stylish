---
type: Styleguide Rule
description: |-
  Attach a span to each unit of work, such as a request, job, or
  connection, with #[tracing::instrument] or .instrument(span), so events
  emitted deep in the call stack and across awaits carry its context. Skip
  large or secret arguments with skip(...).
language: rust
category: observability
rule_id: INSTRUMENT-UNITS-OF-WORK
priority: info
tags:
- observability
- tracing
- async
- spans
- rust-skills
---
Attach a span to each unit of work, such as a request, job, or
connection, with #[tracing::instrument] or .instrument(span), so events
emitted deep in the call stack and across awaits carry its context. Skip
large or secret arguments with skip(...).

## Good

- #[tracing::instrument(skip(self, body), fields(order_id = %order_id))]
async fn submit(&self, order_id: OrderId, body: Bytes) -> Result<Receipt, SubmitError> {
    // ...
}

## Bad

- async fn submit(&self, order_id: OrderId, body: Bytes) -> Result<Receipt, SubmitError> {
    tracing::info!("submitting"); // which order? which request?
    // ...
}
