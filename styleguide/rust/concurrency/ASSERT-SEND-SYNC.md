---
type: Styleguide Rule
description: |-
  Public types, and the futures they return, should be Send (and usually
  Sync). Pin this with a compile-time assertion so a refactor (an Rc, or a
  RefCell borrow held across .await) can't silently regress it.
language: rust
category: concurrency
rule_id: ASSERT-SEND-SYNC
priority: info
tags:
- concurrency
- send
- sync
- compile-time
- beautiful-rust
---
Public types, and the futures they return, should be Send (and usually
Sync). Pin this with a compile-time assertion so a refactor (an Rc, or a
RefCell borrow held across .await) can't silently regress it.

## Good

- const _: () = {
    const fn assert_send_sync<T: Send + Sync>() {}
    assert_send_sync::<Client>();
};

## Bad

- pub struct Client { cache: Rc<Cache> } // silently !Send; downstream spawn() breaks
