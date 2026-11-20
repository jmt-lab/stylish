---
type: Styleguide Rule
description: |-
  Tie test resources such as temp directories, spawned servers, and
  environment overrides to a value whose Drop cleans them up
  (tempfile::TempDir, a guard struct), so cleanup runs even when the test
  panics.
language: rust
category: testing
rule_id: RAII-TEST-FIXTURES
priority: info
tags:
- testing
- fixtures
- raii
- rust-skills
---
Tie test resources such as temp directories, spawned servers, and
environment overrides to a value whose Drop cleans them up
(tempfile::TempDir, a guard struct), so cleanup runs even when the test
panics.

## Good

- #[test]
fn test_store_persists_entries() {
    let directory = tempfile::tempdir().expect("create temp dir");
    let store = Store::open(directory.path()).expect("open store");
    // directory is removed when it drops, even on assertion failure
}

## Bad

- #[test]
fn test_store_persists_entries() {
    fs::create_dir_all("/tmp/store-test").unwrap();
    // ...assertions that may panic...
    fs::remove_dir_all("/tmp/store-test").unwrap(); // skipped on failure
}
