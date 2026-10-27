---
type: Styleguide Rule
description: |-
  Do not recover panics just to avoid crashes; the program state may be
  corrupt or hold locks. When an invariant violation makes state
  unrecoverable, terminate (log.Fatal), and surface failures through
  monitoring.
language: go
category: error_handling
rule_id: NO-RECOVER-TO-HIDE-PANICS
priority: info
tags:
- panic
- recover
- reliability
- google-style
---
Do not recover panics just to avoid crashes; the program state may be
corrupt or hold locks. When an invariant violation makes state
unrecoverable, terminate (log.Fatal), and surface failures through
monitoring.

## Good

- if len(shards) != expected {
    log.Fatalf("shard table corrupt: have %d, want %d", len(shards), expected)
}

## Bad

- defer func() {
    if r := recover(); r != nil {
        log.Printf("ignoring panic: %v", r) // continues with corrupted state
    }
}()
