---
type: Styleguide Rule
description: |-
  Write async tests with #[tokio::test] instead of building a runtime by
  hand. Use start_paused = true (or tokio::time::pause) to test timeouts
  and retries deterministically without real sleeps.
language: rust
category: testing
rule_id: TOKIO-TEST-FOR-ASYNC
priority: info
tags:
- testing
- async
- tokio
- rust-skills
---
Write async tests with #[tokio::test] instead of building a runtime by
hand. Use start_paused = true (or tokio::time::pause) to test timeouts
and retries deterministically without real sleeps.

## Good

- #[tokio::test(start_paused = true)]
async fn test_retry_backs_off_between_attempts() {
    let started = Instant::now();
    let result = with_retry(3, failing_operation).await;
    assert!(result.is_err());
    assert_eq!(started.elapsed(), Duration::from_millis(300));
}

## Bad

- #[test]
fn test_retry_backs_off_between_attempts() {
    let runtime = tokio::runtime::Runtime::new().unwrap();
    runtime.block_on(async { /* real sleeps make this slow and flaky */ });
}
