---
type: Styleguide Rule
description: |-
  Arithmetic that can overflow on untrusted or unbounded input states its
  intent: checked_* when overflow is an error, saturating_* or clamp when
  the value should stop at a bound, and wrapping_* when modular arithmetic
  is the point. Plain + panics in debug and silently wraps in release.
language: rust
category: numeric
rule_id: EXPLICIT-OVERFLOW-HANDLING
priority: warn
tags:
- numeric
- overflow
- arithmetic
- correctness
- rust-skills
---
Arithmetic that can overflow on untrusted or unbounded input states its
intent: checked_* when overflow is an error, saturating_* or clamp when
the value should stop at a bound, and wrapping_* when modular arithmetic
is the point. Plain + panics in debug and silently wraps in release.

## Good

- let total = price
    .checked_mul(quantity)
    .context(OrderTotalOverflowSnafu { price, quantity })?;

- let volume = current.saturating_add(step).clamp(MIN_VOLUME, MAX_VOLUME);

- let hash = hash.wrapping_mul(FNV_PRIME) ^ u64::from(byte); // modular by design

## Bad

- let total = price * quantity; // wraps in release when an attacker sends a huge quantity

- let remaining = budget - spent; // u64 underflow when spent > budget
