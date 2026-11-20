---
type: Skill
name: rust-async
description: >-
  Design and write async Rust services on Tokio that follow the stylish Rust styleguide:
  runtime setup, task layout, channels, shared state, cancellation, timeouts, graceful
  shutdown, tracing spans, and deterministic async tests. Use this whenever the user writes
  or debugs code with tokio, async fn, .await, select!, spawn, channels, or an async
  server, worker, or client, or asks why an async program hangs, leaks tasks, or won't shut
  down. Pairs with rust-best-practices, which covers everything that isn't async-specific.
---

# Rust async (Tokio)

This skill condenses the async rules in `styleguide/rust/concurrency/`, plus the related
testing and observability rules. Rule IDs appear in `CAPS-WITH-DASHES`; read
`styleguide/rust/<category>/<RULE-ID>.md`, or use the argosy `search_rules` tool, when you
need the exact wording. When this file and a rule disagree, the rule wins.

## 1. Decide where the runtime lives

- **Libraries** expose `async fn` and don't pick a runtime, spawn tasks, or install a
  tracing subscriber (LIBRARIES-DONT-ASSUME-RUNTIME, LIBRARIES-NEVER-INSTALL-SUBSCRIBERS).
  If they must spawn, they take a spawner or `Handle` from the caller.
- **Binaries** create the runtime once, in `main`, with `#[tokio::main]`. Use the
  multi-threaded default for servers. Use `flavor = "current_thread"` for CLIs and
  tools that mostly wait on a handful of requests.
- Keep `main` thin (MAIN-RS-BINARY). It sets up tracing, loads config, wires tasks
  together, and runs the shutdown sequence (section 7).

## 2. Lay out tasks as a tree

Every task has an owner that awaits it, and the owner can tell it to stop.

- Spawn into a `JoinSet` or keep the `JoinHandle` (TRACK-SPAWNED-TASKS). A detached
  `tokio::spawn` loses its panics and errors.
- Pass a `tokio_util::sync::CancellationToken` (or child tokens) to every long-running
  task (GRACEFUL-SHUTDOWN).
- Run independent work concurrently with `try_join!` instead of sequential awaits
  (JOIN-INDEPENDENT-FUTURES).
- Use `async fn` everywhere (ASYNC-FN-OVER-IMPL-FUTURE), including in traits
  (NATIVE-ASYNC-FN-IN-TRAITS). Take async callbacks as `impl AsyncFn`
  (ASYNC-CLOSURE-BOUNDS).

## 3. Communicate with bounded channels

| Need | Channel |
|---|---|
| Work queue, many producers, one consumer | `mpsc::channel(capacity)` |
| A single reply to a request | `oneshot` |
| Every subscriber sees every event | `broadcast` |
| Observers need only the latest value (config, health) | `watch` |

- Always bound the queue and name the capacity as a documented const (BOUNDED-CHANNELS,
  NAMED-CONSTANTS). `send().await` is the backpressure.
- Prefer message passing over shared locks (PREFER-MESSAGE-PASSING). An actor that owns
  its state and serves requests over `mpsc` plus `oneshot` replies needs no lock at all.

## 4. Share state carefully

- A shared service is a cheap-to-clone handle around `Arc<Inner>` (CHEAP-CLONE-SERVICES).
  Don't put `Arc` in public signatures (NO-SMART-POINTERS-IN-PUBLIC-API).
- Use `std::sync::Mutex` for short critical sections that never span an `.await`. It is
  faster than the async mutex. Use `tokio::sync::Mutex` only when the guard really must be
  held across an await (NO-LOCK-ACROSS-AWAIT, LOCK-SCOPE-DISCIPLINE).
- Reach for `RwLock` only for measured read-heavy contention
  (RWLOCK-ONLY-WHEN-READ-HEAVY). Use atomics for counters and flags, and justify each
  `Ordering` (ATOMIC-ORDERING-DELIBERATE).
- Assert that public futures and types are `Send` when callers will spawn them
  (ASSERT-SEND-SYNC).

## 5. Never block the executor

- No `std::fs`, `std::thread::sleep`, blocking HTTP clients, or blocking database drivers
  in async code. Use the async equivalents (NO-BLOCKING-IN-ASYNC).
- Send CPU-heavy work (hashing, compression, parsing large inputs) to
  `tokio::task::spawn_blocking` or rayon (YIELD-IN-CPU-BOUND-ASYNC,
  RAYON-FOR-DATA-PARALLELISM).
- Symptoms of a blocked executor are timers firing late, unrelated requests stalling
  together, and `tokio-console` showing long poll times.

## 6. Cancellation, select, and timeouts

- A future can be dropped at any `.await`. Keep invariants intact across awaits: update
  state after the await completes, or use a guard whose `Drop` restores it.
- `select!` drops the losing branches. In a looping `select!`, use only cancel-safe
  operations (`recv`, `read`, `sleep`, `changed`, `cancelled`). Otherwise keep the progress
  outside the loop or pin the future once (CANCEL-SAFE-SELECT).
- Put a deadline on every await that depends on the outside world, through the client's
  timeout or `tokio::time::timeout` (TIMEOUT-EXTERNAL-AWAITS). Retries use bounded attempts
  with backoff.

## 7. Shut down gracefully

```rust
/// Time allowed for in-flight work to finish after a shutdown signal.
const SHUTDOWN_GRACE: Duration = Duration::from_secs(10);
/// Pending jobs buffered between the listener and the workers.
const JOB_QUEUE_CAPACITY: usize = 256;

#[tokio::main]
async fn main() -> Result<(), AppError> {
    tracing_subscriber::fmt().with_env_filter(EnvFilter::from_default_env()).init();
    let config = Config::load().context(LoadConfigSnafu)?;

    let shutdown = CancellationToken::new();
    let (jobs_tx, jobs_rx) = tokio::sync::mpsc::channel(JOB_QUEUE_CAPACITY);
    let mut tasks = JoinSet::new();
    tasks.spawn(run_listener(config.listen_address, jobs_tx, shutdown.child_token()));
    tasks.spawn(run_worker(jobs_rx, shutdown.child_token()));

    tokio::select! {
        signal = tokio::signal::ctrl_c() => signal.context(SignalSnafu)?,
        Some(exited) = tasks.join_next() => {
            tracing::error!(?exited, "task exited before shutdown was requested");
        }
    }

    shutdown.cancel();
    let drained = tokio::time::timeout(SHUTDOWN_GRACE, async {
        while let Some(result) = tasks.join_next().await {
            if let Err(error) = result {
                tracing::error!(%error, "task failed during shutdown");
            }
        }
    })
    .await;
    if drained.is_err() {
        tracing::warn!("shutdown grace period elapsed; aborting remaining tasks");
        tasks.abort_all();
    }
    Ok(())
}
```

Producers stop on cancellation and drop their senders, so consumers see the channel
close and drain what is left. Flush buffered writers and close connections explicitly
before returning (DESTRUCTORS-NEVER-FAIL, BUFFERED-IO).

## 8. Make it observable

- Give each request, job, or connection a span with `#[tracing::instrument]`. Skip large
  or secret arguments (INSTRUMENT-UNITS-OF-WORK, NEVER-LOG-SECRETS). Spans follow a future
  across awaits; thread-local context does not.
- Record values as fields (STRUCTURED-LOG-FIELDS) and log each error once, where it is
  handled (LOG-ERRORS-ONCE-WITH-CHAIN).

## 9. Test deterministically

- Use `#[tokio::test]`. Pass `start_paused = true` to test timeouts, retries, and
  intervals without real sleeps (TOKIO-TEST-FOR-ASYNC).
- Put I/O behind traits or channels so tests can inject fakes (MOCKABLE-IO).
- Test shutdown: cancel the token, then assert that tasks finish and buffered work is
  flushed.
- Check custom synchronization with loom (LOOM-FOR-CONCURRENCY-PRIMITIVES).

## 10. Checklist

- No blocking calls in async code, and CPU-heavy work is offloaded.
- No lock guard or `RefCell` borrow is held across `.await`.
- Every spawned task is owned (`JoinSet` or `JoinHandle`) and observes a cancellation
  token.
- Every channel is bounded and uses the right type.
- Every external await has a timeout.
- Each looping `select!` uses only cancel-safe branches.
- `main` handles ctrl-c, cancels, drains with a grace period, and flushes.
- Libraries don't pick a runtime or install a subscriber.
- Async tests use paused time instead of real sleeps.
