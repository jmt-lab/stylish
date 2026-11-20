---
type: Styleguide Rule
description: |-
  select! drops every branch that loses the race, along with any state
  held inside those futures. Only put cancellation-safe futures in a
  select! that loops (recv, read, sleep, changed), keep partial progress
  outside the select, or pin a non-cancel-safe future once and poll it
  across iterations.
language: rust
category: concurrency
rule_id: CANCEL-SAFE-SELECT
priority: error
tags:
- concurrency
- async
- tokio
- select
- cancellation
- rust-skills
---
select! drops every branch that loses the race, along with any state
held inside those futures. Only put cancellation-safe futures in a
select! that loops (recv, read, sleep, changed), keep partial progress
outside the select, or pin a non-cancel-safe future once and poll it
across iterations.

## Good

- let mut buffer = Vec::new();
loop {
    tokio::select! {
        read = stream.read_buf(&mut buffer) => {
            if read? == 0 { break; }
        }
        () = shutdown.cancelled() => break,
    }
}

- let mut frame = std::pin::pin!(read_frame(&mut stream));
loop {
    tokio::select! {
        result = &mut frame => return result,
        _ = ticker.tick() => report_progress(),
    }
}

## Bad

- loop {
    tokio::select! {
        // read_exact is not cancel-safe: bytes read so far are lost
        // whenever the ticker wins the race.
        result = stream.read_exact(&mut header) => handle(result?),
        _ = ticker.tick() => report_progress(),
    }
}
